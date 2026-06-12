---
title: "Evolution Filter: Help with detail in filter-rule please!"
date: 2009-12-16
forum: General Help
---

### Post by max-julian on 2009-12-16
Hi!

I receive emails which mean work-to-do and (re)move them from my imap-inbox to a local folder when the work is done.
This is done via an imap-account in evolution and evolution's local folder.

Problem: I sometimes forget to move the email, and instead delete it.

Therefore I want to set up a message-filter, which automatically makes a copy of each email. This is already working with this Message filter rule:

If Source Accout is <my-email@address.com>
Then Copy to Folder "local mail archive folder"

Problem with this: all email in this mail archive folder is marked as "unread" and therefore attract my eye's attention via the number writting in bold letters next to the folder-name.
But if I add the action "Set Status Read", then the emails in the Inbox folder are too marked as read, which is not good (new arriving emails _should_ get my attention with a number written in bold letters next to the Inbox-Folder).

So my question is: How do I make a rule to automatically set the archived copy as read, but leave the mail in the inbox as unread (until I read it).


many thanks in advance for any reply!

Max-Julian


PS: I still use Ubuntu 9.04 with all updates there are (Switching to another version of ubuntu is an option).
I use Evolution Version 2.26.1

---

### Post by dcstar on 2009-12-17
> **max-julian said:**
> Hi!

I receive emails which mean work-to-do and (re)move them from my imap-inbox to a local folder when the work is done.
This is done via an imap-account in evolution and evolution's local folder.

Problem: I sometimes forget to move the email, and instead delete it.

Therefore I want to set up a message-filter, which automatically makes a copy of each email. This is already working with this Message filter rule:

If Source Accout is <my-email@address.com>
Then Copy to Folder "local mail archive folder"

Problem with this: all email in this mail archive folder is marked as "unread" and therefore attract my eye's attention via the number writting in bold letters next to the folder-name.
But if I add the action "Set Status Read", then the emails in the Inbox folder are too marked as read, which is not good (new arriving emails _should_ get my attention with a number written in bold letters next to the Inbox-Folder).

So my question is: How do I make a rule to automatically set the archived copy as read, but leave the mail in the inbox as unread (until I read it).


many thanks in advance for any reply!

Max-Julian


PS: I still use Ubuntu 9.04 with all updates there are (Switching to another version of ubuntu is an option).
I use Evolution Version 2.26.1

It seems the "Unset" rule doesn't work to reset the Read status, so I don't know if this should be reported as a bug.

---

