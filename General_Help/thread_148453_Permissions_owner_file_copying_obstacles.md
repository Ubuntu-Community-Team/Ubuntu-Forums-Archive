---
title: "Permissions /owner file copying obstacles"
date: 2006-03-22
forum: General Help
---

### Post by Delboy2 on 2006-03-22
I don't have windows installed but I have Ubuntu 5.10 installed on my Toshiba Portege (hda3 ext2 partition) which installed fine but which i am still evaluating other smaller live distros on this machine. I am having loads of trouble trying to copy these other distro .iso files from my pcmcia attached cdrom to my hard disk.  Cd-rom is recognised and mounted already. Problems are thus:
When logged in as user, I can copy and paste _some _files from the rom drive to my root (ubuntu , home) partition but I get permission error messages for files such as kernels or .fs data files when trying to transfer some of these iso files and the copy paste fails.  They typically have a red cross on them when viewed in Nautilus.  Logged in as user, I also cannot copy anything across to the hard disk hda1 DOS partition - the intended destination for these files.  
To write to this hda1 partition I need to log out and reboot in recovery mode (as root) I can copy to hda1 but some files copied over previously as user are now out of bounds because I am not the owner.  As root in recovery mode, my pcmcia cd-rom is not mounted for some strange reason so I can't copy directly from the rom to hda1.
I have tried every terminal command line for password / root changing etc. in the 'help' section and those I have found on this forum but they don't work so:
I just want to copy freely from partition to partition in Nautilus (as user or root)without any issues of write permissions or 'ownership'.  How do I erradicate these security protocols please?  A simple step by step advice for a newbee would be most appreciated.
I am persevering with Ubuntu as it is the only distro I have come across which boots properly and automatically configures my pcmcia cdrom but  
the solution at the moment seems to be to buy and install a copy of windows 2000 to allow me to carry out these simple tasks.

---

### Post by chuckyp on 2006-03-22
Try "sudo -s"  that will give you a root prompt.  You would be able to copy the files then in that terminal.

---

### Post by goatflyer on 2006-03-22
Edit your /etc/fstab file and change the entry for /dev/hda1 as follows:

```

/dev/hda1       /media/hda1     vfat    umask=000      0       0

```

Note: this is UNSAFE if your dos partition is ntfs.  That issue has to do with the fact that ntfs is not documented, the linux people have reversed engineered it enough to be able to read, which is always safe.  Some people report that they CAN write to ntfs partitions, but I'll wait until my distro supplier tells me so first.

---

### Post by Delboy2 on 2006-03-22
Hda1 is Fat16 with Dos 6 on it not NTFS.
Thanks for the replies Goatflyer and Chuckyp I 'll give both a go tonight.  Chuckyp is there any way I can do this copying from within Nautilus and not command line in terminal?
Again, this forum comes up with help almost immediately.

---

### Post by Delboy2 on 2006-03-23
I think I've cracked this:  When logged in as user, do "sudo -s" at the terminal, enter your password, then at the root prompt that will appear, type:
"gksudo nautilus". This will open up Nautilus as root and ownership locking seems to disappear.  I can now copy some of these problem files to hda1.
If you leave the terminal root prompt and open up Nautilus from the desktop you will be back, as user, at square 1.

---

