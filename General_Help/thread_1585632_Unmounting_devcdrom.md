---
title: "Unmounting /dev/cdrom/"
date: 2010-09-30
forum: General Help
---

### Post by Genesis W on 2010-09-30
I am trying to install a game on Ubuntu using Crossover games and come with the issue with this message.

This disk contains two sections, one for Mac and one for Windows.  In order for CrossOver to use this disk it must be mounted so that the Windows portion is visible.

To make this change, remount as root with this command:
mount -t udf -o users,ro,unhide,uid=1000 /dev/cdrom "/media/cdrom0"

I automatically am told I need to be root so I add sudo in front. 

This time /dev/sr0 is already in the way of mointing it so I try unmounting it with [SIZE=2]umount          /dev/sr0/ and then enter the command [/SIZE]mount -t udf -o users,ro,unhide,uid=1000 /dev/cdrom "/media/cdrom0" again and get the same message that /dev/sr0/ is int the way.

What should I do?

---

### Post by mc4man on 2010-09-30
Don't know anything about crossover, do use wine for a couple of things.
the combo of no fstab entry(s) for cd/dvd drive(s) and the silly security bit policy have had a poor effect on wine in general and the use of cd's to install things.

Myself I've taken to just creating the standard static mountpoint(s) and adding the drive(s) back in fstab with the typical previous mount options which resolved all issues here.

you may wish to consider doing that.

(if so post this - ignore warning about super-user
```
lshw -C disk
```
and this (put in a code box when posting
```
cat /etc/fstab
```

---

