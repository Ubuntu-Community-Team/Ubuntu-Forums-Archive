---
title: "WDC WD30EZRS-00J99B0 and AMD SB750 RAID - Windows and Linux interaction issue ..?"
date: 2011-02-16
forum: General Help
---

### Post by ghost_zero on 2011-02-16
Hi,

I got a 3TB drive today the WDC WD30EZRS-00J99B0 and I have an AMD SB750 RAID controller (in RAID mode) active.
I then tried to create a full partition using GPT which worked fine (using gparted) to create this and make sure alignment (4KiB sector size) is fine.
I then rebooted and tried to open that partition under Windows and there I ran into the issue:
According to Windows the drive was not partitioned at all (it doesn't even have GPT. 
OK, so I tried to create that partition under Windows which worked fine but then Ubuntu said that there is no partition table.
So I was only able to get it to work on one of them.

I then used the included controller card for the HDD and there it works fine on both Windows and Linux, so I guess it is some kind of Windows driver issue?

I already tried updating the SB 750 RAID driver to 3.1.1540.151 (before I had 3.1.1540.81) which I think is the latest one - was available in the 10.10 Catalyst version (but is from 2009), it isn't included in the 10.11 anymore.

I have tested this by using Ubuntu 10.10 and Windows 7 Home Premium - both 64 Bit.

---

### Post by ghost_zero on 2011-02-16
OK. I am not sure yet but I think this might be related to this issue:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/599255](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/599255)

---

### Post by srs5694 on 2011-02-16
I recommend you do this:


[list=1]
[*]Download the Linux and Windows versions of GPT fdisk (gdisk) from its [Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) and install both versions in their respective OSes.
[*]Use gdisk to view your partition table in both OSes. Under Linux, launch it by typing "sudo gdisk /dev/sda" (or whatever the device filename is for the disk); in Windows, it would be "gdisk 0:" (or a higher number) from an Administrator command prompt. Type "p" to view the partition table.
[*]Pay attention to the disk size in sectors reported by the utility in both OSes.
[*]If gdisk reports there are no partitions and if you're willing to repartition, create some partitions, type "w", and view the partition table in both OSes.
[/list]


By comparing what the same program reports in two different OSes, you'll get a better idea of what's going on. If gdisk reports that the disk is a different size in one OS than in another, you can be pretty sure that there's some weird driver issue going on. If gdisk reports identical disk sizes and partition tables in both OSes but Windows refuses to acknowledge the partitions, then perhaps something weird is going on with the Windows GPT code.

---

### Post by ghost_zero on 2011-02-18
As it works fine with the included HPA.
Which is why I don't think that it is the Windows GPT code but I might try this later. I am currently doing some other tests with those HDDs which will take a while.

---

