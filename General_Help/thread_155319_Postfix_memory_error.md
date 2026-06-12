---
title: "Postfix memory error"
date: 2006-04-04
forum: General Help
---

### Post by thorndike on 2006-04-04
Good evening folks,

I have a server running Kubuntu5.10 that is configured to email me the results of some backup activities.  Over the last several days, the backups ran, but the notifying emails first were sent blank, then stopped coming altogether.

When I checked the mail logs I found this:

postfix/sendmail[15457]: fatal: gethostbyname: Cannot allocate memory
postfix/sendmail[15458]: fatal: gethostbyname: Cannot allocate memory
postfix[17401]: fatal: gethostbyname: Cannot allocate memory

and on and on and on.

I tried stopping and restarting postfix, but that had no effect.  The moment it tried to start I got the above errors.

This worked just fine before.

Thorndike

---

