---
title: "Mounting an External XFS Drive"
date: 2012-10-11
forum: General Help
---

### Post by Mctoot on 2012-10-11
Hi Guys,

bit of a n00b here just need a little help trying to identify if I am doing something incorrectly when mounting a USB external drive formatted in XFS.

I am typing:

*sudo mount -t xfs /dev/sdb1 /media/external*

And I get the following error:

*mount: wrong fs type, bad option, bad superblock on dev/sdb1, missing code page or helper program or other error In some cases useful info is found in syslog*

I have this external HDD which is written in XFS and connected to a External Network hard drive which allows me to view and use in windows. Last night it just stopped showing the content. I can still see it in the Network HDD GUI and in windows device management and in ubuntu but the only options they are all giving me (expect ubuntu because I havent worked out how to access it yet) is to format it. I do not want to do this as I have almost 2TB of info I want to keep!

Any help would be great and much appreciated.

---

### Post by sienile on 2012-10-11
Is Windows failing to recognize it also? I would suspect a filesystem error if so. If that's the case you will need a data recovery program to try to salvage your files.

---

### Post by LewisTM on 2012-10-11
You should attempt to repair it.
Install xfs utilities
```
sudo apt-get install xfsprogs
```
Then run a filesystem repair
```
sudo xfs_repair -v /dev/sdb1
```
See [FONT="Courier New"]man xfs_repair[/FONT] for more options
Something to take into consideration:
> **Disk Errors**
**xfs_repair**  aborts  on  most disk I/O errors. Therefore, if you are trying to repair a filesystem that was damaged due to a disk drive failure, steps should be taken to ensure that all blocks in the filesystem are readable and writeable before attempting to use xfs_repair to repair the filesystem. A possible method is  using  **dd**(8) to copy the data onto a good disk.
Good luck!

---

### Post by Mctoot on 2012-10-12
Ok the repair seemed to work.

I can now see the USB drive after I mounted it. Only now it is asking me to clean it. Will this remove the data? And if Not how do I do this?

---

### Post by Mctoot on 2012-10-12
All good I deleted the log data from the drive and ran the repair again and boom she works... Thank you so much for your help!

---

