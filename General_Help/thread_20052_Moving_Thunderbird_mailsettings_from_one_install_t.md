---
title: "Moving Thunderbird mail/settings from one install to another"
date: 2005-03-14
forum: General Help
---

### Post by dougr on 2005-03-14
I plan on doing a clean install of Hoary.  I upgraded from Warty to Hoary, but have just screwed too much stuff up and just want to start over fresh.  I have most of the things together I need to move, but am confused with thunderbird.  What folders/files to I need in order to import my email and settings into the fresh install?

Thank You,
Doug

---

### Post by Joeb on 2005-03-14
Save or backup a copy of the .mozilla-thunderbird directory.  It has all of your email and settings.  After the new install, but before you run thunderbird, copy the .mozilla-thunderbird directory back to your new home directory.

That should do it.

Joeb

---

### Post by jsgotangco on 2005-03-15
like what mentioned above, the contents of that folder can be used to migrate even thunderbird emails from the windows version to linux version and vise-versa. It's pretty nifty.

---

### Post by plantman on 2007-10-21
I am trying to move Tbird from Feisty to Gutsy. I am a new newbie and need specific instructions.:confused:

---

### Post by itsjustarumour on 2007-11-20
> **Joeb said:**
> Save or backup a copy of the .mozilla-thunderbird directory.  It has all of your email and settings.  After the new install, but before you run thunderbird, copy the .mozilla-thunderbird directory back to your new home directory.

That should do it.

Joeb

OK, I've done that, and everything is working swimmingly - apart from one thing.  When I delete items, they don't show up in my "Deleted Items" folder - they're just gone!  I've been through all the settings and preferences but can't see anything that would cause this.

Has anyone else had this problem?  Any ideas how to fix it?

EDIT - using Gutsy with latest Thunderbird from the Ubuntu repos btw.

---

### Post by itsjustarumour on 2007-11-21
> **itsjustarumour said:**
> OK, I've done that, and everything is working swimmingly - apart from one thing.  When I delete items, they don't show up in my "Deleted Items" folder - they're just gone!  I've been through all the settings and preferences but can't see anything that would cause this.

Has anyone else had this problem?  Any ideas how to fix it?

EDIT - using Gutsy with latest Thunderbird from the Ubuntu repos btw.

Bump.

---

### Post by Joeb on 2007-11-23
> **itsjustarumour said:**
> OK, I've done that, and everything is working swimmingly - apart from one thing.  When I delete items, they don't show up in my "Deleted Items" folder - they're just gone!  I've been through all the settings and preferences but can't see anything that would cause this.

Has anyone else had this problem?  Any ideas how to fix it?

EDIT - using Gutsy with latest Thunderbird from the Ubuntu repos btw.

Are you talking about deleted mails not showing up under the Trash folder in Thunderbird or are you talking about when you delete a file through the nautilus, it no longer ends up in your deleted files folder in your user directory?

Joeb

---

### Post by itsjustarumour on 2007-11-23
> **Joeb said:**
> Are you talking about deleted mails not showing up under the Trash folder in Thunderbird or are you talking about when you delete a file through the nautilus, it no longer ends up in your deleted files folder in your user directory?

Joeb

Hi Joeb,

I was refering to the "Deleted Items" folder in Thunderbird.  Anything I delete from my Inbox seems to be removed completely rather than going to the Deleted Items folder.  I've checked all the settings/preferences and everything is set correctly...

---

### Post by Joeb on 2007-11-23
> **itsjustarumour said:**
> Hi Joeb,

I was refering to the "Deleted Items" folder in Thunderbird.  Anything I delete from my Inbox seems to be removed completely rather than going to the Deleted Items folder.  I've checked all the settings/preferences and everything is set correctly...

Do you have a folder titled "Deleted Items"?  If so, how about "Trash"?  My Thunderbird  puts deleted messages in the "Trash" folder.  If you do have a Trash folder and the messages aren't being placed there it might be one of two things.

If you delete messages and they never make it to the trash folder, right click on the folder and go to the "retention property" tab and make sure it's not set to delete read messages immediately.  Mine is set to use the server defaults which is not to any delete messages (that way, the trash is emptied only when I tell it to be emptied).

If the messages make it to the trash folder but are gone the next time you log in to Thunderbird, go to the edit menu, then account settings and on the "Local Folders" option, make sure the "Empty Trash on Exit" is not checked (unless you do want to empty the trash on exit).

If you don't have a Trash folder, try creating one under the Local Folders. and then see if your deleted messages start going there.  

Joeb

---

