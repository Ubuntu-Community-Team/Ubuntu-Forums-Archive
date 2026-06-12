---
title: "Evolution: old emails not visible after changing IMAP settings"
date: 2011-12-30
forum: General Help
---

### Post by beakdan on 2011-12-30
Hi-

I'm running Maverick, and have two accounts that I use for evolution: my personal email account (which is the default Inbox, etc) and a work email account (which has a separate Inbox under [email]my.name@mywork.com[/email]).  This issue concerns my work email.

We are changing to MS Exchange, and so had to update my IMAP settings.  Previously I logged in to the server "imap.mywork.com", using my email address as the login.

Now, under Exchange, I log in to a different server, "exchangeimap.mywork.com", with a user ID (as opposed to email address).

The migration was made last night, so this morning, I put in the new settings, clicked download, and ended up with 3 new emails in the [email]my.name@mywork.com[/email] Inbox.  The only problem is that my OLD emails are now invisible.

I checked ./evolution/imap/, and there are two folders:
[email]my.name@mywork.com@imap.mywork.com[/email]
[email]userID@exchangeimap.mywork.com[/email]

The old emails are still in the "my.name" folder; I can open them with a text editor.

Presumably the issue is that Evolution doesn't know these two folders are the same, but I'm not sure how to merge them.  Would it be as simple as copying all the contents from the "my.name" folder to the "userID" folder?

Any help appreciated,
Dan

---

