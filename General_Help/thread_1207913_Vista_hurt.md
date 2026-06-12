---
title: "Vista hurt?"
date: 2009-07-08
forum: General Help
---

### Post by setari on 2009-07-08
Alright so I installed Ubuntu, but I think I may have hurt my windows vista installation, is there any way to actually access my vista installation so that i can roll back (system restore) to a point where Ubuntu hasn't even touched my computer, or what? I cannot find my Vista CD, and was hoping there was a tchnical way to do it.


Also, for future reference if I dont find my vista CD and there is no way to restore vista, I have an external hard drive, and ubuntu doesn't recognize it. How can I get ubuntu to recognize the EHD? ty!

---

### Post by Roasted on 2009-07-08
Ubuntu doesn't recognize the external hard drive? Really?? Ubuntu recognizes FAT file systems as well as NTFS... I find it strange Ubuntu wouldn't pick it up. If you go to terminal and type sudo fdisk -l, do you see a secondary hard drive there? Perhaps it pulled a device ID (example - /dev/sdb1) but it didn't have a mount point to get fully loaded on Ubuntu. Just an idea...

Also - About your Vista partition - how did you install Ubuntu? Did you command Ubuntu to dump on top of the entire disk, erasing everything? Or did you have spare space behind the Vista install on the hard drive where you told Ubuntu to install?

If Ubuntu was installed on top of Vista, your Vista install is gone. There won't be any way to initiate a system restore because the operating system itself won't even be functional to get to that point. Doing a system restore with Ubuntu on the drive will not in turn wipe Ubuntu so it's as if Ubuntu was never on your computer. A system restore is operating system dependent. AKA a Vista system restore will effect Vista only - not Ubuntu.

The only possible way you could restore your computer to the way it was prior to you installing Ubuntu on it is if you happened to make an image if your hard drive prior... which means you take a "snapshot" of your install and store it externally from the computer. If you have that, you could re-upload it to your computer, which would wipe your computer however the image would become your primary boot media which would retain the exact same operating mode as it did prior to you making the image. 

HOWEVER - If you didn't make an image, this option is not possible.

So, some questions that need answered are - how did you install Ubuntu? On top of the entire drive? On spare space on the hard drive? Does Vista still exist? Did you overwrite it? When you boot up does it go right to Ubuntu or do you have a dual boot option?

---

### Post by ddrichardson on 2009-07-08
Rollback will only work for changes in Vista, did you install Ubuntu from CD or via Wubi (the program you run in Windows)?

If you open a terminal and enter the following commands and paste the output here we can afford more help:```
sudo fdisk -l
```

For the external drive, plug it in then type```
dmesg
```Post any messages that talk about USB or USB Storage.

---

