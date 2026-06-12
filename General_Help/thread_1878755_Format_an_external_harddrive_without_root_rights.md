---
title: "Format an external harddrive without root rights"
date: 2011-11-10
forum: General Help
---

### Post by danielsbrewer on 2011-11-10
I am on a work machine where I do not have root rights.  I have an external harddrive that is formated ext3 but I cannot write to it as the user permissions are different.  I would like to start afresh and format the drive, but I cannot find any way to format it without root access.  Any ideas?

---

### Post by proxx1850 on 2011-11-10
Uhm yeah , I believe disk-utility can do this kind of things without root permission.

And otherwise why not pop in a cd/usb key and do the job from there.

:)

---

### Post by danielsbrewer on 2011-11-10
Can't see any sign of disk-utility.  Maybe the admins have removed it.

Yes I thought about using a live USB key but I can't seem to be able to install without root permission (but maybe I am missing something).  I don't have any blank CDs :(.

---

### Post by proxx1850 on 2011-11-10
See if you can run "palimpsest" without quotes from the run dialog Alt-F2 or terminal.
If not they indeed removed it.

I am pounding my brain here, but i think your pretty much screwed, if you cant install anything else.
Partitioning most of the time does require higher privs.
Mounting ext3 iirc does require privs as well.
Iam not an expert though.

---

### Post by WorMzy on 2011-11-10
Anyone can mount filesystems, assuming that udisks is installed and the user belongs to the right group.

Formatting partitions, however, requires root privileges. At least, as far as I know. Can you imagine how much damage an uneducated end-user could do if they could format partitions?

---

### Post by danielsbrewer on 2011-11-10
Luckily I found a USB stick with gparted on so I have been saved.  Thanks for the input.

---

### Post by danielsbrewer on 2011-11-10
I suppose another option might have been to boot up in safe mode.

---

