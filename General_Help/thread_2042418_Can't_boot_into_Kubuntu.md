---
title: "Can't boot into Kubuntu"
date: 2012-08-14
forum: General Help
---

### Post by Charcoalcat on 2012-08-14
I've been dual-booting Kubuntu and Windows 7 for a couple of weeks and I've been able to boot into Kubuntu just fine until this afternoon. Now when I choose Kubuntu's entry, instead of the regular bootloader I get the grub prompt screen saying "Minimal BASH-like line editing is supported.", etc. ls in that prompt yields the contents of my C drive.

I've tried using the live CD to run boot-repair twice to no avail. This is the link to the paste from the first time I tried: [http://paste.ubuntu.com/1147414/](http://paste.ubuntu.com/1147414/) I tried again after creating a new partition to use as a boot partition. This is the paste I got after that: [http://paste.ubuntu.com/1147492/](http://paste.ubuntu.com/1147492/)

I can't think of anything I've done that'd make the bootloader suddenly stop working; Windows ran chkdsk last night but I booted into Kubuntu once after that. Help would really be appreciated; I really don't want to struggle through reinstalling Kubuntu yet again.

---

### Post by Charcoalcat on 2012-08-16
I've reinstalled a bunch of times now and continue to get the same grub prompt. I tried following the instructions on [this page]("http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/") and now I get a grub rescue prompt saying error: no such partition. ls shows my Windows partitions only, but I've booted into the Kubuntu live CD and my other partitions are definitely there. I've searched up this error but it only seems to happen for people who have uninstalled Ubuntu, and I haven't. Does anybody know what I could do to fix this?

edit: Here is the latest BootInfo summary, if it's needed: [http://paste.ubuntu.com/1150811/]("http://paste.ubuntu.com/1150811/")

---

### Post by YannBuntu on 2012-08-16
Hello
As indicated by Boot-Repair, you probably need a separate/boot partition at the start of your disk.
See [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by Charcoalcat on 2012-08-16
Thank you for the reply. I'm unable to shrink my C: drive to less than 100 GB and I've heard that moving the Windows SYSTEM partition or C: partition would cause errors. Kubuntu used to work for me with the same setup without a /boot partition - would this mean that creating a /boot partition wouldn't solve the problem? I'm very reluctant to try moving the SYSTEM and/or C: partitions.

---

### Post by YannBuntu on 2012-08-16
This may be a GRUB regression ([https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1030887)), so alternatively you can try installing an older version of GRUB2, eg [http://packages.ubuntu.com/oneiric/grub-pc](http://packages.ubuntu.com/oneiric/grub-pc)

---

### Post by Charcoalcat on 2012-09-02
I'm sorry I left this thread for so long. I was hoping I would be able to just get used to Windows.

I don't have much experience with Ubuntu and I'm not sure how to install an older version of GRUB from the live cd. I tried downloading the package you linked and opening the .deb file, but it said error: cannot satisfy dependencies. Could someone possibly outline the steps for me? It would be much appreciated.

---

### Post by Charcoalcat on 2012-09-02
Sorry for the double post... I tried booting into Kubuntu again shortly after posting that and it suddenly worked. I haven't changed anything since I last tried, so I don't know why that happened, but I expect it'll suddenly stop working again just like last time, and the operating system seems to have been incorrectly installed, so I guess I don't really want to bother with that. I'll just stick with my Windows that works.

---

