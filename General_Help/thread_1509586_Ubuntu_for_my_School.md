---
title: "Ubuntu for my School"
date: 2010-06-14
forum: General Help
---

### Post by Cactusm123 on 2010-06-14
I've just about gotten my school convinced to switch to Linux instead of upgrading to Windows 7 (from XP), but there's a few things that need to be covered first.

Firstly, the Windows machines currently auto-mount a network drive at login for each student. Would it be possible to have each user's home directory be on a server and accessed through the network? 

Secondly, the school uses Autodesk programs for the engineering courses. Will those run in Wine, or would we need to dual boot/virtualize Windows? If we need Windows for that, how would they access the home directory from above?

Thirdly, the school has about 500 computers throughout the district. Is there a better way of installing on all of them than booting each from a CD (Imaging from a source on a server, perhaps?), and how would I go about doing that?

Fourthly, the internet at the school is filtered. Is there a way to filter the internet through a Linux server?

Finally, users don't have the privileges to write to the computer's hard disk, only the network drive.  Can an entire drive be set to read only, with programs set to execute?

Thanks for your time,

Ethan Miller

---

### Post by emarkay on 2010-06-14
Good start here, may not get instant replies on this. May want to go directly here:
[http://www.ubuntu.com/support](http://www.ubuntu.com/support)

1. I am sure this is possible, don't have specifics.

2. I know that CAD progs are one main area where Linux lags - have you looked at Intellicad (Acad clone)  in Wine?  Do not know any further , but for Wine issues go here directly:
[http://appdb.winehq.org/index.php](http://appdb.winehq.org/index.php)
There's 362 pages of apps that do, almost and don't work in Wine. 

3. See #1.  ;) 

4. That can be a browser specific setting, or you meaning total network IP address blocking?

5. A good thing - something like "DeepFreeze" in Win - IMHO, if they can't "SUDO" they can't mess with the OS level of things, but that doesn't prevent bookmarks and email settings, and document settings and all that.  Maybe there's a way to "clone" the "HOME" partition each AM to "restore" it to new from a known good master.

Just wanted to chime in - sorry I don't know more!

Good luck!

MRK

---

### Post by Cactusm123 on 2010-06-14
4. I was referring to total IP blocking. For example, YouTube can only be accessed by teachers. Which brings the question to light - how would that work?

5. The school uses deepfreeze now, and hates it, mostly because they have to jump through a million hoops to install software. How would post-installation software distribution work? Could new software be pushed out, or be selectively installed from the software center?

Again, thanks for your time. Bringing Linux to schools is bringing Linux one step closer to the world.

---

### Post by hhoyt on 2010-06-14
re: homedirectory to server, one solution is NFS. ref:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Cheers, Howard

---

