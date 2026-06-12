---
title: "Help with NVIDIA RAID"
date: 2009-11-11
forum: General Help
---

### Post by Lethithan on 2009-11-11
OK, I have Windows Vista on a RAID 0, handled by a NVIDIA thing on the motherboard, on two 500gb drives, partitioned into three(NTFS). And Ubuntu on a separate 200gb.
I haven't been able to find a way to access my files on the 1tb array, I looked up DMRAID and it got GPARTED to recognise it (finally). 
However whenever I try to mount it, it doesn't show up in Computer, Mount tells me that it has been mounted.
I also played with MDADM for hours beforehand.

This is the only problem I have with keeping Linux as my main OS.

Any help on what I need to do next would be appreciated.

---

### Post by alphaniner on 2009-11-11
> However whenever I try to mount it, it doesn't show up in Computer, Mount tells me that it has been mounted.

Where does mount say it has been mounted?  What happens if you go to that location?

---

### Post by Lethithan on 2009-11-11
/dev/mapper/nvidia_gedgadbh3 on /dev/sdd type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

I also noticed in System Monitor that if I double-click the linux drive it opens up, but this one won't.

Edit: Sorry, it's mounted on what appears to be a file, opening it does nothing.

---

### Post by alphaniner on 2009-11-11
When it is mounted like that, what is the output of **fdisk -l**?

---

### Post by Lethithan on 2009-11-11
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a1f36d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102400000    7  HPFS/NTFS
/dev/sda2           12749       25497   102400000    7  HPFS/NTFS
/dev/sda3           25497      121603   771971072    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       23330   187398193+  83  Linux
/dev/sdc2           23331       24321     7960207+   5  Extended
/dev/sdc5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdh: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       77825   625129281    7  HPFS/NTFS

---

### Post by alphaniner on 2009-11-11
I was hoping there would be an entry for /dev/sdd there...

Sorry, I got nothing else.

---

### Post by Lethithan on 2009-11-11
Thanks for trying.

---

### Post by alphaniner on 2009-11-11
Have you looked through [this]("https://help.ubuntu.com/community/FakeRaidHowto")?

---

### Post by Lethithan on 2009-11-11
Ok it's working now, I mounted them to folders in /dev/mapper/ and It seems to work fine.

Thanks for your assistance.

---

