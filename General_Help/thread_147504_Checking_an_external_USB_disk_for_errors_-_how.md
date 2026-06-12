---
title: "Checking an external USB disk for errors - how?"
date: 2006-03-20
forum: General Help
---

### Post by smalldeus on 2006-03-20
A little help needed here :) I have an external USB disk formated in ext3. I would like to be able to check it for errors like I used to do it in Windows with chkdsk. How do I do that? :confused:

---

### Post by grendel_khan on 2006-03-20
Have you tried running 'fsck /media/usbdisk', assuming your USB disk is mounted as /media/usbdisk? You may have to remount it as read-only; I'm not certain. If it complains that the disk is mounted read-write, and that checking it is terribly dangerous, you might be able to 'mount /media/usbdisk -o remount,ro' to make it read-only.

Let me know if that works for you; I don't have a USB disk here to test it with.

---

### Post by smalldeus on 2006-03-21
Shouldn't the disk be completely unmounted for checking it? :-k  If it's readonly, how will the check fix any problems it finds? Thanks for the info, I'll try to work with your tips :)

---

### Post by kosmic on 2006-03-21
Yes the disks should Be always Unmounted,.  :)

---

### Post by smalldeus on 2006-03-21
Well, I tried doing it but it doesn't work. Here is the output from the comandline:

[INDENT]smalldeus@dusty:~$ fsck /media/usbdisk/
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: Is a directory while trying to open /media/usbdisk/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/INDENT]

The disk is mounted on USBDISK - but the command doesn't return the right error - it should be telling me this is dangerous to do if the disk is still mounted :-k Since I don know much about UNIX commandlines - help :confused:

---

