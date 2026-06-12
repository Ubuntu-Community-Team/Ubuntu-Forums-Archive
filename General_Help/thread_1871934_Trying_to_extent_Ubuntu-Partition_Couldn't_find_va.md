---
title: "Trying to extent Ubuntu-Partition: Couldn't find valid filesystem block"
date: 2011-10-29
forum: General Help
---

### Post by JohannesJo on 2011-10-29
Im currently trying to extent my Ubuntu-partition as there is almost no space left. After having some issues ([http://ubuntuforums.org/showthread.php?t=1870560](http://ubuntuforums.org/showthread.php?t=1870560)) I get this warning in gparted:

```

e2label: No such file or directory while trying to pen /dev/sd5
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.41.14 (22-Dec2010)
dumpe2fs: No such file or directory whole trying to open /
dev/sd5


```
[IMG]http://dc98.2shared.com/download/HfBuOK-j/gparted.png?tsid=20111029-214956-d7091d05[/IMG]


fdisk -l gives me this:
```
/dev/sda1            2048    20482047    10240000   27  Hidden NTFS WinRE
/dev/sda2   *    20482048   262116539   120817246    7  HPFS/NTFS/exFAT
/dev/sda3       323532800   625137663   150802432    7  HPFS/NTFS/exFAT
/dev/sda4       282585087   323532799    20473856+   f  W95 Erw. (LBA)
/dev/sda5       282585088   306780159    12097536   83  Linux
/dev/sda6       306782208   315146239     4182016   82  Linux Swap / Solaris
/dev/sda7       315158528   323532799     4187136   82  Linux Swap / Solaris

```How should I proceed if I want to exent sd5 by the unallocated space without loosing any data?

---

### Post by ajgreeny on 2011-10-29
Are you using a live CD to do this?  All your linux partitions are within the extended sda4 partition, so you will not be able to do anything from your running installed ubuntu as sda4 will have to be mounted to run ubuntu.  It is just not possible to do that.

However, I am confused.  You appear to have a 12GB linux root (presumably) partition, and for some reason two 4GB swap partitions.  Why two?  And there does not seem to be huge amounts of unallocated space on the disk, though it would be simpler if we could see a screenshot from gparted.

I think you could certainly delete the first of the two swap partitions and use the remaining one for your installation's linux partition, but that will still give you only a maximum extra space of about 4GB;  is that enough for you?

I think I need more information please about your exact wishes, and that screenshot please.

---

### Post by dFlyer on 2011-10-29
"How should I proceed if I want to exent sd5 by the unallocated space without loosing any data?"

You will have to delete one of your swap files as it looks like all you space allocated. Why 2 swap files?

---

### Post by JohannesJo on 2011-10-29
Thanks for your reply. I was using an ubuntu live-cd and the error wont show up when the system is regulary booted. I cant resize anything there as well though (not even the windows partitions).

The screenshot:
[IMG]http://img1.UploadScreenshot.com/images/main/10/30119020534.png[/IMG][/URL]

I supose that the second swap was created during a reinstallation of ubuntu. Can I safely remove it? And if, how should I do it?

---

### Post by JohannesJo on 2011-10-29
If I try to remove the inactive swap I get the message that the Ressource is currently used ("Failed to add partition 4").

---

### Post by ajgreeny on 2011-10-30
Those two swap partitions will be found and used by a live CD.  You need to right click on them and use the swapff option, and proboably also the extended sda4 and choose unmount.

---

### Post by JohannesJo on 2011-10-31
> **ajgreeny said:**
> Those two swap partitions will be found and used by a live CD.  You need to right click on them and use the swapff option, and proboably also the extended sda4 and choose unmount.

That did the job. I tried it out yesterday. After swaping off, I was able to resize sda4 which somehow solved gparted issues about sda5.

Thank you!

---

