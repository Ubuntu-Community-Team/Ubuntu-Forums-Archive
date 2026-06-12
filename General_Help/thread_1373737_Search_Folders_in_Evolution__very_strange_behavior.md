---
title: "Search Folders in Evolution : very strange behavior"
date: 2010-01-06
forum: General Help
---

### Post by Dougga on 2010-01-06
So I wanted to create something that is pretty standard in the computer world: a search folder that shows me all the unread email in both local and remote (IMAP: Ubuntu/Postfix/Dovecot) folders.

Creating the folder was easy enough.
1. Create Search Folder
2. Edit properties to find: "Status is not Read"

Viewing the folder was a bit of a nightmare.

If I clicked on any email that was unread, the email would appear for a moment, it's status would then change to 'read', it would then vanish, the next unread email would come up and then vanish.  All unread email would then be flipped through until there was none in the search folder.

I now have to go through all of my folders to make sure I haven't missed any important emails.

Is there a way to create a rational search folder for unread mail given this setup?

Thanks

---

### Post by dcstar on 2010-01-06
> **Dougga said:**
> So I wanted to create something that is pretty standard in the computer world: a search folder that shows me all the unread email in both local and remote (IMAP: Ubuntu/Postfix/Dovecot) folders.

Creating the folder was easy enough.
1. Create Search Folder
2. Edit properties to find: "Status is not Read"

Viewing the folder was a bit of a nightmare.

If I clicked on any email that was unread, the email would appear for a moment, it's status would then change to 'read', it would then vanish, the next unread email would come up and then vanish.  All unread email would then be flipped through until there was none in the search folder.


Turn off the auto marking as read feature.

---

### Post by Dougga on 2010-01-06
So the solution is to force a manual process for marking email as read?
I think I understand.  Generally I like the mail client to keep track of what email I've read.  This is a pretty basic feature.  I wonder how Microsoft handles this in Outlook.  I've used it for so long I never really thought about the logic.

---

### Post by donato roque on 2010-01-06
There is a very easy solution for you.  There's an option above the email pane.  It says All Messages.  Click it.  There should be an option for Unread Messages.  Evolution will only show you Unread messages.

You don't need to create a search folder.

---

### Post by Dougga on 2010-01-06
> **donato roque said:**
> There is a very easy solution for you.  There's an option above the email pane.  It says All Messages.  Click it.  There should be an option for Unread Messages.  Evolution will only show you Unread messages. You don't need to create a search folder.

Actually, that feature will only show you the unread messages in the currently viewed folder.  I'm looking for ALL unread messages that have landed in other folders via filters.

Thanks

---

