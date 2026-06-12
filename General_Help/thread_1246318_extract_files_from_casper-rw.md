---
title: "extract files from casper-rw"
date: 2009-08-21
forum: General Help
---

### Post by dslowik on 2009-08-21
Does anyone know of any tools to extract or get into the persistent casper-rw file from a Live USB drive.  I've got a Live USB drive based off of 9.04 that will create some log files which get saved into the casper-rw file.  I will need to need to plug this drive into a Windows machine and be able to get the log files off.

I had also considered making another partition and save the log file to it, but I found out that Windows will only allow you to get to one partition on a removeable drive.

Any help or suggestions would be appreciated.

---

### Post by dandnsmith on 2009-08-21
loop-mount the casper-rw, and then you can copy/modify the contained files to your hearts content.

eg.
*mount -o loop casper-rw-1000M /mnt/odd2fs/*

BTW it's an ext3 filesystem, if that helps

---

### Post by dslowik on 2009-08-21
Thanks, I'll see what I can do with that.

---

### Post by Tshann on 2010-06-20
This is an old post, but the command *"mount -o loop casper-rw /media/mnt"* (Had to change it a bit for my circumstance) totally worked for me. I needed it to mount the persistent casper-rw from a ubuntu pendrive install to get some files. Worked awesome. Thanks

---

