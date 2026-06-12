---
title: "Exchange mail filtered out in Evolution"
date: 2009-12-18
forum: General Help
---

### Post by haydentech on 2009-12-18
I am using Evolution 2.28.1 on Ubuntu 9.10.  I am connected to an Exchange 2007 mail server via evolution-mapi (0.28.2).

When the mail is first retrieved, all my mail shows up in my Inbox.  This lasts a few seconds only, when there appears a task in the status bar at the bottom of the window which says something like "Filtering Inbox".  While this process is ongoing, I can browse and view all my mail.  When that process completes, I'm left with only 8 of my 497 messages which were originally in the Inbox.  The issue is that I can't figure out what is doing the filtering, or how to stop it.  The 8 e-mails left don't seem to have any connection to one another, other than it's the same 8 each time if I recreate the account from scratch.

The "Show" menu is set to "All Messages".  The "Search" box is clear (i.e. no entry in there).  Nothing is going to my Junk e-mail box.  There are no message filters checked, and anyway, I have the "Apply filters to incoming messages" setting turned off anyway.  When I view my account with Outlook, all the mail is there, so the Evolution filtering has no effect on Outlook.

What is this filtering that is going on, and most importantly, how do I stop it?

---

### Post by dcstar on 2009-12-19
> **haydentech said:**
> 
.........
The "Show" menu is set to "All Messages".  The "Search" box is clear (i.e. no entry in there).
.........


Is it set to "All Accounts"?

---

### Post by haydentech on 2009-12-21
Even after deleting the account in Evo, I noticed that the account was still listed in the .evolution directory in my home directory.  Once I manually deleted that, creating the account again worked and the mailbox was not erroneously filtering all the mail.  There must have been some piece of stale info in the mailbox directory that was screwing it up.

---

