---
title: "Mount query"
date: 2010-04-24
forum: General Help
---

### Post by srikris on 2010-04-24
I have installed ubuntu along with windows.
There are two users in ubuntu. when one user mounts windows drive, the other user is unable to access it .
What shud i do so that all the users access windows drives?

Thax in advance
Sri

---

### Post by SnickerSnack on 2010-04-24
Did you try making the mount point a shared folder so that maybe the second user can access it as 'network location'?

---

### Post by Denis Cruze on 2010-04-24
check the permission of the mount or add the users in one group and give the mount the group permission.

---

### Post by srikris on 2010-04-24
Iam naive user, so Please explain me more clearly. 
It is not a folder it is the windows D drive and how can i make it as network location?

As i right clicked on drive->properties-> permissions, it gives permissions of drive couldnt be determined (Is it due to it belongs to windows OS)?

How can i resolve it?

Thanx
Sri

---

### Post by SnickerSnack on 2010-04-24
When you mount a device (partition, iso image, ...), you have the device itself, say, /dev/sda1, and you have a _mount point_, say, /mnt/windows.  So the computer makes a sort of link between the two so that _the contents of /dev/sda1 can be found in /mnt/windows_.

Now, we mean that you should change the permissions on /mnt/windows.*

It would be possible to just make that folder open to everyone, but that's not the best way to do it.

Make a new group:
1) Go to the menu, System>Administration>Users and Groups.
2) Click on the lock and enter your password.
3) Click Manage Groups.
4) Click Add Group.
5) Name the group (maybe 'windows') and check both users.
6) Click 'close'; click 'close'.

Now change the group permissions on the folder**:
1) Open a terminal.
2) type "cd /mnt", enter
3) type "chgrp [groupName] [folderName]", with the names in place of bracketed items.
4) In the graphical file manager, navigate to /mnt.
5) Right click on 'windows'.
6) Click "Permissions".
7) Change 'Group Folder Access' to "Create and delete files".
8) Click 'close'.

==>> Now both users should be able to use that folder, and therefore, both should be able to use the windows partition when it is mounted there.

*You probably want to use whatever mount point you have been using rather than making a 'new' one since that could have hassles of its own.

**(I tried to do this only through the gui, but for some reason, "windows" wasn't showing up as a group that folder could be changed to, so either rebooting would fix it, or you really have to use the command line.  I hope the directions are clear enough.)

---

