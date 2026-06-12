---
title: "Help saving my system"
date: 2010-04-21
forum: General Help
---

### Post by sandys on 2010-04-21
Hi there,

I applied an update of some software I cannot recall and now my system won't boot up.

I see a quick flash of the ubuntu flash screen (a white symbol) and then it hangs.

I've tried numerous kernel choices at boot with no joy, the recovery console boots so far (to initramfs prompt) but I cannot access my disk to get data off of it, or at least I don't know how too.

Any tips, is there any other info that might be helpful?

How can I access my disc and what options do I have for getting up and running again, been using Ubuntu for over 18 months now and have enjoyed using it but now its not working i've not got a clue, currently running off of a live disc, it won't allow me to access my driver either strangely?

If I was running windows, I would of just re-installed over the top and not lost any data, can I do similar with the live disc.

I'm Running 9.10 UNR on a EEEPC 1000H

---

### Post by oldsoundguy on 2010-04-21
Make sure the Grub bootloader is  available:
[http://www.easy-ubuntu-linux.com/grub-menu-visible.html](http://www.easy-ubuntu-linux.com/grub-menu-visible.html)

then re-boot .. and run the repair option of the current kernel first.

IF that fails, you can select an older kernel instead.

---

### Post by sandys on 2010-04-21
I assume the menu with kernel options and recovery mode is the grub menu, I already get that, the recovery option does not work.

I get some messages as it boots

EXT4-fs(sda1) ext4_check_descriptors: Inode bit????(cant read my writing) for group 640 not in group (block ????????)
EXT-fs(sda1) group descriptors corrupted

and 

target filesystem doesn't have /sbin/init

then the machine enters a busybox shell and I have access to udev /dev and some limited commands, the prompt says initramfs

I still can't directly access my disk, tried to cd to /dev/sda1 with no joy but tried cat /dev/sda1 and it started spewing stuff to the screen, so its there and not dead.

---

### Post by no2498 on 2010-04-21
do not know if this will help but
go down to next to the bottom kernel an try the fix

i hope it helps you

---

### Post by sandys on 2010-04-21
thanks but tried every option bar the memtests of course, no joy :(

---

### Post by klemes on 2010-04-21
It seems to me like hard disk failure or massive data corruption at best(just a polite way to say your hdd has gone AWOL) .In any way I think your Ubuntu installation is not recoverable by any means.
Is your EEEPC still under warranty???
If so contact your supplier explaining what happened.

P.S.Only thing you can do since on LiveCD is to open a console and type:

sudo fdisk -l

that will reveal your partition table and then do a fsck /dev/sdaX (substitute X with the numbers of the partitions you want to check : all except the swap partition).Quiet possibly without any true results but it's the only thing you can do for now.

---

### Post by sandys on 2010-04-21
cheers, that put me on the right path, did a search and came up with this

[http://ubuntuforums.org/showthread.php?t=1150032](http://ubuntuforums.org/showthread.php?t=1150032)

So yup, sounds like disc corruption alright.....bugger.

---

### Post by sandys on 2010-04-21
Its alive :guitar:

ran 

sudo fsck -f /dev/sda1 

manually allowed it to fix lots of stuff I can't even pretend to understand and blindy said yes to it all, not sure what might be lost but at least some stuff is recoverable.

---

