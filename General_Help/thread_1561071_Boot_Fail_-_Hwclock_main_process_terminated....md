---
title: "Boot Fail - Hwclock main process terminated..."
date: 2010-08-25
forum: General Help
---

### Post by Mashepherd on 2010-08-25
Using Ubuntu 10.04, System working fine up until this morning when I turned my computer on and it failed to boot; instead sending my to a screen saying

Hwclock main process (340) terminated with status 2...

To the best of my knowledge I hadn't changed anything prior to this problem arising

Very Confused???!

---

### Post by quizno50 on 2010-08-25
That is very strange... Does it say anything else? Can you still boot into the live-cd?

---

### Post by Mashepherd on 2010-08-26
Powered back up my pc this morning and this is what appeared to be on screen;

init: hwclock main process (222) terminated with status 23dc5
Filesystem check or mount failed
A maintenenace shell will now be started.
CONTROL-D will termiante this shell and continue booting after re-typing filesystems. Any further errors will be ignored
root@mypcname:~#_


After pressing CONTROL-D it desplays this rather nice looking message;

init: hwclock main process (261) terminated with status 2
Mountall start/starting
Filesystem check or mount failed
A maintenenace shell will now be started.
CONTROL-D will termiante this shell and continue booting after re-typing filesystems. Any further errors will be ignored
root@mypcname:~#_


Anyhelp? (i'm very confused!)

---

### Post by quizno50 on 2010-08-26
Looks to me like it's trying to do a disk check and it's unable to so it's dropping you into a maintenance shell. You might try running fsck manually.
```
fsck -f /dev/sda1
```
You might need to change /dev/sda1 to whatever your root (/) hard disk partition is.
After running this you should be able to press Ctrl+D (maybe have to hit it a few times) to tell ubuntu to keep booting.

---

### Post by chakdefatte on 2010-09-01
well, try using *mountall start*..atleast this should get you up to the login page, you may encounter further errors there.. 
Then you might be able to login but the desktop might not load, then you can proceed with the normal troubleshooting..or if you get errors, try logging in with a different environment, maybe xbuntu or any other, not gnome..depending on which flavor you are using..atleast if you have 2 or more environments, I think you be able to login to the desktop..
My understanding says that this problem happens when you are dual booting with windows, or unknowingly you remove a mount point which was there during last boot..

---

