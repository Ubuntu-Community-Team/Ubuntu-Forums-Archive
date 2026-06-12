---
title: "Thunderbird sends PDFs as application/x-msdownload"
date: 2012-03-30
forum: General Help
---

### Post by abovett on 2012-03-30
Hi

Some people are unable to receive PDF attachments sent via Thunderbird from Ubuntu because it's sending them as MIME type application/x-msdownload instead of application/pdf

When sending from Windows the problem doesn't occur.

Has anyone else come across this? Any known solutions?

Thanks

Andy

UPDATE 5th April 2012

I have found the solution. The "attachments" section in the options had two entries for PDF, and one was for application/x-msdownload. Deleting this entry solved the problem. Apparently these options control how attachments are sent as well as how they are handled when received.

Hope that helps anypne else with the same problem.

Andy

---

