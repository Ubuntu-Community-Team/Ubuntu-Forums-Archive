---
title: "How do you detect a new hard drive in Ubuntu?"
date: 2009-08-04
forum: General Help
---

### Post by Bradj47 on 2009-08-04
I just installed a new 20 GB IDE hard drive and I was wondering how to check if theres anything on it. If there was does it show up merged with all the other documents under root? Or does it show up as a separate device somewhere?

---

### Post by merlinus on 2009-08-04
You will probably have to mount it.

```
sudo fdisk -l
```may show you the hdd, filesystem, and partition(s).  Post results if you need more assistance.

---

### Post by NightwishFan on 2009-08-04
I believe if the disk is there, it may show up in nautilus with any partitions. However I never actually tried this myself, so I do not know. If it detects it you definitely should be able to mount it manually.

---

### Post by Bradj47 on 2009-08-04
> **merlinus said:**
> You will probably have to mount it.

```
sudo fdisk -l
```may show you the hdd, filesystem, and partition(s).  Post results if you need more assistance.

Here are my results: 
```

brad@rockstar:/opt$ sudo fdisk -l
[sudo] password for brad: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000586a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9402    75521533+  83  Linux
/dev/sda2            9403        9729     2626627+   5  Extended
/dev/sda5            9403        9729     2626596   82  Linux swap / Solaris

Disk /dev/sdb: 2044 MB, 2044198912 bytes
63 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
brad@rockstar:/opt$ 

```

I thought I deleted the partition with Solaris on it but that's off topic. Is the second disk /dev/sdb? To access it do I just cd to /dev/sdb?

---

### Post by Bradj47 on 2009-08-04
Ok, cd /dev/sdb didn't work. Here's a previous post I made that is related to this issue: [http://ubuntuforums.org/showthread.php?t=1231293](http://ubuntuforums.org/showthread.php?t=1231293)
I really need help with that.

---

### Post by merlinus on 2009-08-04
sda5 is a swap partition, used by ubuntu.  Don't worry about the solaris label.

Linux uses partitions, not drives, except for usb flashdrives, cd/dvd drives, and such, so you will need to format sdb using gparted on the live cd, or you can install it:

```
sudo apt-get install gparted
```and then you will find it in System/Administration/Partition Editor.

---

### Post by Hobgoblin on 2009-08-04
> **Bradj47 said:**
> I just installed a new 20 GB IDE hard drive and I was wondering how to check if theres anything on it. If there was does it show up merged with all the other documents under root? Or does it show up as a separate device somewhere?

If it has a valid filesystem on there then it should be listed under places.  Clicking it should then cause it to be mounted under /media

---

### Post by dcstar on 2009-08-05
> **Bradj47 said:**
> I just installed a new 20 GB IDE hard drive and I was wondering how to check if theres anything on it. If there was does it show up merged with all the other documents under root? Or does it show up as a separate device somewhere?

Install the **pysdm** package, create a new mount point for your drive somewhere (do **not** use /media as that is a system folder for removable media) and mount it there using the tool you just installed.

---

