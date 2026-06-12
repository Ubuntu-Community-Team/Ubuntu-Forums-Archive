---
title: "Hard Drive read only after ubuntu crashed"
date: 2010-03-13
forum: General Help
---

### Post by WinterWeaver on 2010-03-13
I was busy making backups to my external hard drive just now, but Ubuntu crashed 10 mins into the backups. After rebooting the affected folders are now Read only, and I cannot add or remove anything.

This is extremely annoying, I already threw away two USB flash disks because the same thing happened to me in the past.

I don't want to throw away the external because it's far more expensive and packed with backups.

Any assistance in fixing the drive would be greatly appreciated.

Symptoms: I can write or delete a file to the hard drive, in any folder, accept the folders that was being accessed when the computer crashed.

I have tried to change permissions, but I get an error.
I tried opening a terminal and sudo rm -r that folder, but I get a input/output error.

I'm running Karmic.
Backups were made by Back-in-time

Regards,

---

### Post by tom4everitt on 2010-03-13
Hmm, what about a complete reformating? Can be done in for example gparted.

---

### Post by WinterWeaver on 2010-03-13
I have a lot of backups on this drive.... cannot just format.
Also, reformatting my usb flash disks didn't work, which is why I ended up throwing them away.

---

### Post by bzhao on 2010-03-13
what kind of format is the problem partition?
if it is windows(fat fat32, ntfs),please use Window os to fix the file system in it,
if it linux (ext2,ext3,ext4), please umount that partition under Linux(commandle:sudo umount /dev/sdxx ),and then use fsck coommand to fix the file system and then remount again or resert the usb disk. try again.

---

### Post by WinterWeaver on 2010-03-14
It's a windows drive, since I need to use it over multiple systems. Thanks for the suggestion to use windows to fix the file system. It never actually occurred to me to try that, since I'm always in linux :)

Will see how I get along.

Regards

Andre

---

