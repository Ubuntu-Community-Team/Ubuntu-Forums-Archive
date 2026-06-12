---
title: "Moving tmp partition - GDM special files problem"
date: 2011-08-14
forum: General Help
---

### Post by cryptotheslow on 2011-08-14
Hi :)

I'm in the process of moving /tmp out of the root filesystem to it's own (larger) partition.

From a LiveCD I've:
1. Created the new part (ext4 format and is /dev/sda4)
2. Mounted the installed OS root filesystem (/dev/sda1) as /slash
3. Mounted /dev/sda4 as /newtmp
4. Using gksudo nautilus I'm trying to copy the contents of /slash/tmp to /newtmp

I have 4 files that won't copy - returning the error "Can't copy special files".

These are related to ORBit it seems:

/slash/tmp/orbit-gdm/linc-4f5-0-7d450f3fee846
/slash/tmp/orbit-crypto/linc-5f0-0-521bd890aa0ed
/slash/tmp/orbit-crypto/linc-632-0-7a7ac5bac09ed
/slash/tmp/orbit-crypto/linc-634-0-47b154cad0b0d

Looking at them the are Type: socket (inode/socket)

Questions are:
a. Will GDM or ORBit fail if I start up without these?
b. Or will they just be recreated on the fly if found to be missing?
c. What's the best way to proceed??

Many thanks in advance :D

---

### Post by cryptotheslow on 2011-08-14
I found the answer to my own questions :D

So for those wondering... by default Ubuntu clears /tmp on every boot so copying the files across from the old /tmp was unnecessary.

I just renamed the old /tmp to /tmpOLD and added the fstab entry to mount /dev/sda4 as /tmp.

Rebooted and was confronted with a libgconf sanity-check-2 error and was unable to login.

Had to switch to a terminal and chmod the permissions of the new /tmp to be the same as the (now) /tmpOLD. Mode required was 1744 if I remember rightly.

Everything working fine now and survived a reboot :)

Thanks for reading :)

---

