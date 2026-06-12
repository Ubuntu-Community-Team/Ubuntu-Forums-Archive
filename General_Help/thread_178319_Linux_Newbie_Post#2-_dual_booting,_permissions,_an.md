---
title: "Linux Newbie Post#2- dual booting, permissions, and drivers"
date: 2006-05-17
forum: General Help
---

### Post by caybo on 2006-05-17
Thanks, you guys were so much help i decided to post here again. Thanks I got my Avast on linux working, first installed program.

     I am dual booting.  It works fine( I think ) I can choose using the grub boot menu either XP or Linux.

_*Dual Booting hard drive* Thing # (1)_ on my desktop is an annoying hda1, and it is my windows XP hard drive.  I dont want it there.  I dont have permission to do anything to it.  ITS STUCK.
What should i do?

_*Permissions*-Thing # (2)_ i put file system on my desktop as that has everything on it.  When i go into there i cant modify anything, it says im not the owner.  It is lying.
What should i do?
_*Drivers?*-Thing #(3)_ I installed ubuntu, and everything looks, sounds, and performs perfectly fine.  But i am confused.  Unlike windows i havent installed any drivers for my hardware.  Do i still need too.  Is it any different on linux? how do I do it if i do have to?

Thanks all Youve all been great :rolleyes:

---

### Post by Ramses de Norre on 2006-05-17
1) Mount it under /mnt instead of /media or turn off the volumes with gconf-editor /apps/nautilus/desktop/ (uncheck volumes_visible).

2) All system files are owned by root, this is for your own safety and makes that for example programs you're running can't change system files (e.g. some virusses do this in windows). You can get root priviliges through [sudo]("http://wiki.ubuntu.com/RootSudo").

3) Yes, you do, but for a lot of normal hardware the drivers are loaded allready. Don't worry about them if everything works fine ;)
Just graphics drivers might be worth to look at, search the forums for your type of video card.

---

### Post by caybo on 2006-05-17
Thanks Alot! youve been a lot of help

---

### Post by Irony on 2006-05-17
Do it like this.

To get XP off the desktop move its mount point from media to mnt (you can move it anywhere you like but this is the usual place);

[PHP]sudo umount /media/XP

sudo mv /media/XP /mnt/XP[/PHP]

Then alter your XP fstab entry from;

[PHP]/dev/hda1       /media/XP  ntfs    nls=utf8,umask=0222 0       0[/PHP]

to;

[PHP]/dev/hda1       /mnt/XP  ntfs    nls=utf8,umask=0222 0       0[/PHP]

Then do;

[PHP]sudo mount -a[/PHP]

Which will refresh your fstab to mount XP in /mnt. Note XP is the name of whatever the name of your actual mount folder is.

---

