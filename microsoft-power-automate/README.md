## Power Automate Workflow Experiment

I tried to design a custom workflow on Power Automate to post an adaptive card to Teams, collect a response, and then write the result into a SharePoint list.

What I designed:
- Recurrence trigger to start the flow.
- Post adaptive card and wait for a response (Teams).
- Handle the response payload and generate a record key.
- Write the data into SharePoint.

Why it failed:
1. A single flow cannot contain more than one trigger, so I could not keep both the schedule trigger and the response trigger in the same flow.
2. Splitting it into two flows (request + response) also failed because the response-collection trigger depends on the output of the request step, so the second flow cannot start.
3. Even when I tried to hedge this by using Microsoft Forms, the data still had to be stored in SharePoint, but the SharePoint SSO login was often invalidated without a clear reason.
