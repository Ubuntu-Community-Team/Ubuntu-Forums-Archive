---
title: "FAT: invalid media value (0x25)"
date: 2009-09-09
forum: General Help
---

### Post by mike-pds on 2009-09-09
Hello everyone -

I am a newbie working with Ubuntu and I recently loaded Ubuntu on a machine, with nagios, and some other tools.  I created a backup of the system and then copied this backup file, bkup.tar.gz, to a usb drive formatted with FAT32 (The usb drive size is 512MB and it's a Microsoft based usb drive).  What I am trying to do is restore this bkup.tar.gz file from the usb, to a computer with a base Ubuntu installation, to make the installation of Ubuntu and nagios quicker and easier.  

Everything worked up until the point where I attempted to mount the usb device, /dev/sdb1, to a computer where I wanted to try to restore the bkup.tar.gz file.  I entered the command mount /dev/sdb1 /mnt and got a message saying I must specify the filesystem type, I then tried mount -t vfat /dev/sdb1 /mnt, and I got an error of FAT: invalid media value (0x25).  I looked into desg : tail and within this file it said FAT:invalid media value (0x25), and the next line says VFS: Can't find a valid FAT fileystem on dev sdb1.  

I'm assuming the issue might be that the partition file is corrupt, but at this point I have no idea what the issue is.  I had no issue mounting this usb drive to the original computer that I made the backup file off of.  Are there some installation packages I might be missing which could be causing this problem?  Does anyone have any idea what the problem might be?  

Thanks for your time.

---

### Post by mike-pds on 2009-09-09
any ideas or is this in the wrong forum?

---

