---
title: "Permissions for drive mounted by FSTAB"
date: 2010-06-11
forum: General Help
---

### Post by grindboy on 2010-06-11
Hi Gang,

OK here is my sordid tale! I've recently done a fresh install of 10.04 dual booted with Windows 7. I Have 2 internal drives so I've decided to stick my OSes on one drive and use the other drive as data.

Thanks to some help from the guys on this forum I've managed to auto mount the drive into my home folder (/home/michael/Data)

Initially when I did this my fstab mounted the Drive with the "Defaults" argument. This however mounted the drive as root and didn't allow me to edit the contents of the drive.

My Fstab now reads:
```
/dev/disk/by-uuid/6732-CECC	/home/michael/Data vfat 	users,umask=0000	    0	    0
```

Now the drive mounts as user and the contents are deletable by user. But the permissions are root. So for example when I download the Evernote windows installer and go to change it to executable so WINE can install it I am unable to change it because the permissions are root.

I've tried running nautilus as root and changing the permissions of both single files on the drive and the drive itself to user but I get:

> Sorry, could not change the owner of "FILE OR FOLDER NAME HERE": Error setting owner: Operation not permitted

Using Chown to change the permissions also gives the same result:

> chown: changing ownership of `/home/michael/Data': Operation not permitted

The only thing I can think off it that something that FSTAB is doing when mounting it is causing these issues.

Hope you guys can help.

Grindboy

---

### Post by dcstar on 2010-06-12
> **grindboy said:**
> Hi Gang,

OK here is my sordid tale! I've recently done a fresh install of 10.04 dual booted with Windows 7. I Have 2 internal drives so I've decided to stick my OSes on one drive and use the other drive as data.

Thanks to some help from the guys on this forum I've managed to auto mount the drive into my home folder (/home/michael/Data)
........

Use the **pysdm** package to mount drives.

---

### Post by grindboy on 2010-06-13
And that is why I love Linux. There is allways a solution. Even when that solution is trying a different method to achieve the same ends!

Thanks DCStar :-)

---

### Post by dino99 on 2010-06-13
mountmanager is my friend, dont like headhaches

---

