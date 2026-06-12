---
title: "How do I go back to windows?"
date: 2010-02-23
forum: General Help
---

### Post by sincerelyydavid on 2010-02-23
i have ubuntu, no dual-boot. how do i go back to windows? just pop in the windows cd and boot from there?

---

### Post by zeroseven0183 on 2010-02-23
How do you want Windows to work? Do you want it to work side-by-side with Ubuntu or just Windows alone?

If you want to have Windows only, just "pop" the CD and it proceed with the installation. It will remove all the data on the partition (still depends on the choice you make).

But if you want to have them both, follow the instructions here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sincerelyydavid on 2010-02-23
i just want to have windows only.
i put in the cd but it doesn't boot. grub loaded instead. it's already set to boot from a cd.

---

### Post by lyall on 2010-02-23
do you want to save any data or files?
if so burn them to a CD/DVDs first

so you want to go back to Windows - right
will here goes

first wipe the hard drive
second use fdisk to set the drive up from floppy or CD
third boot to the Windows CD and install it

after you installed Windows and set it up
install anti-virus program, cleaners for adware, spyware and all that good old stuff  and clean it at less once a month or more


hope to have you back in the Linux world some day :)

good luck and have fun learning

---

### Post by zeroseven0183 on 2010-02-23
I believe Windows installation CDs are bootable. If your BIOS is set to boot first on CD then there's no problem wiping the whole drive off. The Windows CD will format it before it installs the OS.

---

### Post by ajgreeny on 2010-02-23
If you really want to do it, boot to the ubuntu live CD, open System-> Administration-> Gparted and delete all the partitions on your hard disk.  Now use the windows install disk or recovery disk, whichever you have, and install windows again.

Your problem is that when ubuntu is installed to the whole disk, there is no space or partition to install to, windows not being able to see the linux filesystems.  Delete them and you should be OK,

---

### Post by tacantara on 2010-02-23
When you use gParted to wipe the hard drive, be sure to reformat the drive to NTFS, otherwise the Windows install disk will not recognize the drive.

---

### Post by oldfred on 2010-02-23
Please, Please You have 7 posts in the last 24 hours asking basically the same question and everyone is trying to help but you are getting different answers in every thread as the questions are not quite the same.

---

### Post by sincerelyydavid on 2010-02-23
> **oldfred said:**
> Please, Please You have 7 posts in the last 24 hours asking basically the same question and everyone is trying to help but you are getting different answers in every thread as the questions are not quite the same.
sorry, guys. i was freaking out because of the grub rescue screen, didn't know what i was doing. i eventually went back on ubuntu because none of my windows cds work. oh well, guess i'd have to deal with ubuntu. =x

---

