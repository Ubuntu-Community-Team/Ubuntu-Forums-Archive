---
title: "Lock-ups, flashing, don't know what to do"
date: 2011-03-24
forum: General Help
---

### Post by t0p on 2011-03-24
I'm using 10.10 on an EeePC 701.  / is on the 4GB SSD, /home is on an 8GB removable SD card.

It's been running fine for some time.  But in the past couple of days, after the computer has been on for a while I start having lock-ups, menus flash when I try to use them, and right-clicking on objects won't work.

Through some trial and error, I've learned that removing then replacing the SD card (on which /home is mounted) fixes the problem... for a while.  But I want to fix it properly.

Using an Ubuntu live usb, I unmounted /dev/sdc1 then ran fsck on it, with following results:

> 
ubuntu@ubuntu:~$ umount /dev/sdc1
ubuntu@ubuntu:~$ sudo fsck /dev/sdc1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sdc1: clean, 5553/489600 files, 1325730/1956543 blocks (check in 4 mounts)


If the problems start when I'm using the netbook (without live usb) I've tried running fsck on that card and I get a response that the specified superblock does not exist!  Which makes me think maybe there's a problem with the actual card and not the file system.

Can anyone suggest a way to fix this?  Or do I have to go buy a new SD card?  I'm using an 8GB card, and they're not particularly cheap, so I'd like to avoid that if at all possible.

Cheers.

---

### Post by Peter09 on 2011-03-24
I believe that SD cards are not very reliable in the long run for major usage, such as the way you are using. You mist probably are having media failure problems.

---

### Post by t0p on 2011-03-24
> **Peter09 said:**
> I believe that SD cards are not very reliable in the long run for major usage, such as the way you are using. You mist probably are having media failure problems.

Could be.  But now I've noticed the symptoms sometimes appear when I'm using the live usb.  Maybe the netbook is just getting old and arthritic and I need to buy a new mobile device.  A friend of mine recently bought a tablet running Android, and that looks pretty interesting.

What really bugs me is that my desktop must be about 10 years old and it still works fine.  Modern devices seem to be designed to self-destruct soon after the warranty expires.  I hate the modern electronics manufacturing industry!! :(

---

