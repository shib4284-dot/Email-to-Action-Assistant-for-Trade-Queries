PRD: Email-to-Action Assistant for Trade Queries
Author: Shib Kumar Mohanty | Status: Draft v0.1 | Date: 18 Oct 2026
1. Overview
An AI-native workflow that reads incoming trade emails (shipment status, document requests, payment issues), classifies and prioritises them, extracts key identifiers, looks up shipment data, and drafts a reply or creates a task. A human approves anything the model is not confident about.
2. Problem
Exporters, importers and their operations teams handle a large volume of repetitive, email-based queries such as "Where is my shipment?" or "Please resend the packing list for INV-2026-004." Each one requires someone to read the email, find the shipment, check documents, and write a reply. This is slow, error-prone, and pulls people away from higher-value work. Urgent or payment-related emails can get buried in the inbox.
3. Users
• Primary: trade operations executive at an exporter or importer who answers shipment and document queries daily.
• Secondary: finance or compliance team member who needs payment and amendment emails routed correctly.
4. Goals and non-goals
Goals
• Correctly classify incoming trade emails into a small set of categories.
• Extract shipment and invoice IDs and urgency.
• Draft accurate replies from a shipment database for routine queries.
• Escalate uncertain cases to a human rather than guess.
Non-goals (v1)
• Sending emails automatically without approval.
• Reading attachments or real customs and banking integrations.
• Handling languages other than English.
5. User journey
1. An email arrives in the inbox view.
2. The assistant shows the category, urgency, extracted IDs and a confidence score.
3. For routine queries it drafts a reply using the shipment record.
4. The user chooses Approve, Edit, or Escalate.
5. The action and outcome are logged for later review and improvement.
6. MVP requirements
#
Requirement
Priority
1
Classify emails: shipment status, document request, payment issue, amendment, other
Must
2
Extract shipment ID, invoice number and urgency as structured JSON
Must
3
Look up the shipment in a SQL table and draft a reply
Must
4
Route low-confidence or unknown-ID emails to a human review queue
Must
5
Review screen (Streamlit) with Approve, Edit, Escalate
Must
6
Log every decision for evaluation
Should
7
Basic dashboard of categories and escalation rate
Could
7. Wireframe (v1, described)
Left panel: inbox list with category and urgency tags. Right panel: email text, extracted fields, shipment record, draft reply, and the three action buttons.
8. Data
All data is synthetic: 30 to 40 labelled sample emails and a table of 10 to 15 fake shipments. No real company, customer or bank data is used.
9. Success metrics
• Classification accuracy against the labelled set (target to be set after the first baseline run).
• Share of ambiguous or unknown-ID emails correctly escalated instead of auto-answered.
• Draft acceptance rate: share of drafts approved without edits.
• Time per query compared with a manual baseline (estimated).
10. Risks and mitigations
• Wrong reply sent to a customer: human approval is required in v1.
• Model invents shipment details: replies use only database fields, and a missing ID is flagged, never guessed.
• Misclassified urgent emails: urgency keywords plus a confidence threshold route doubtful cases to review.
11. Plan
• Week 1: synthetic data, classification and extraction prompts, database lookup.
• Week 2: review UI, evaluation, README and results.
12. Open questions
• What confidence threshold should trigger escalation?
• Which additional email categories matter most to real users?
• How should attachments be handled in a later version?
