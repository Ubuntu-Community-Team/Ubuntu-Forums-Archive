---
title: "Problem with GID of group?"
date: 2009-11-29
forum: General Help
---

### Post by Roasted on 2009-11-29
I have a folder owned by jason:samba. The permissions of this folder (named test) are 770.

Samba members are:

Jason
Curt
Tyler
Pam

"User" is not a member of Samba. 

Two groups:

Samba - GID of 1005
Samba1 - GID of 1007

If Samba is applied to the test folder, User can read/write/delete.
If Samba1 is applied to the test folder, User is restricted appropriately.

I even switched the names, and the same consistency still exists.

In short: I've discovered the group ID of 1005 is having a problem applying the proper permissions. What in the world is up with this?

---

### Post by Roasted on 2009-11-29
I have no idea what the problem was, but it's fixed now. I was trying to troubleshoot this problem at like 5 am last night so I don't know if that was my issue or not. I also forgot how you have to reboot an XP machine each time you make changes like that, because when I make changes on the file server (my linux box), the connection with windows is still active. Once the XP box reboots, it drops that connection, then when it powers up it re-grabs it when I log in. THEN I take down the new changes to the group rights.

I guess that's what it was. I only remember rebooting the XP box once or twice last night. But it's fixed now and I'm using my Samba 1005 group.

---

