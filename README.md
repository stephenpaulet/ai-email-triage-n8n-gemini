AI-Powered Customer Request Triage

A no-code automation workflow that reads incoming customer messages and automatically classifies them by urgency, category, and a one-line summary using n8n and the Google Gemini API

What it does
Instead of a human reading every customer email and manually deciding what it's about and how urgent it is, this workflow does that triage automatically:
1.	Input: a customer message is received (simulated here; in production this would come from a live mailbox, CRM, or support form).
2.	Prompt: the message is sent to Gemini with an instruction to classify it and return structured JSON.
3.	Output: Gemini returns a result structured in the following way:
	{
 	 "urgency": "high",
	  "category": "delivery",
	  "summary": "Customer is demanding a refund for an undelivered package."
	}
This output can then be routed automatically, logged to a spreadsheet, used to trigger an alert for high-urgency cases, sent to the right team based on category…

Why this matters
Manual email triage doesn't scale and is inconsistent: urgent messages can sit unread in a crowded inbox. Automating the first read means every message gets classified instantly and consistently, and humans only spend time on cases that are already sorted and prioritized. The same pattern extends easily to other repetitive business processes: support tickets, lead qualification, document intake.

Tools I used to build it:
•	n8n: visual workflow builder connecting each step (trigger → data → API call → parsed output)
•	Google Gemini API — handles the actual language understanding and classification
•	Prompt design — the prompt explicitly constrains Gemini to return only valid JSON in a fixed schema, making the output directly usable by downstream steps without extra parsing logic

Files overview:
My workflow.json: the full exported n8n workflow (API keys removed; add your own Gemini key via n8n Credentials or the request URL to run it).
See workflow-canvas.png for a visual of the node structure, and sample-output.png for an example run.

What I'd improve for actual scaling and using it:
•	Replace the manual trigger with a real inbound source (mailbox webhook or CRM event)
•	Add error handling for cases where the model doesn't return valid JSON
•	Store results in a database or spreadsheet automatically (Google Sheets…)
•	Add a routing step that acts on the classification (Slack alert for high-urgency messages)

About
Built as a hands-on introduction to integrating LLM APIs into business-process automation connecting an AI model to a broader workflow rather than using it in isolation.

By Stephen Paulet — LinkedIn
<img width="451" height="686" alt="image" src="https://github.com/user-attachments/assets/3dd788a0-b5fe-49d7-8fae-bfaa5ba63b6a" />
