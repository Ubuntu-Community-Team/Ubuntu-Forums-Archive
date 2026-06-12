---
title: "Shared files between Ubuntu 11.04 and Windows 7"
date: 2011-10-03
forum: General Help
---

### Post by maverick678 on 2011-10-03
I've installed as dual boot, how can I share files between the two ?.

Thanks in advance.

---

### Post by Toz on 2011-10-08
Option #1:
Use a memory key formatted as FAT32. Both systems will be able to access it.

Option #2: 
Create another partition on your hard drive and format it FAT32.

Option #3:
Linux can access NTFS drives. To get Windows to access Linux partitions, you'll need a program like [http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows").

Option #4:
Use a network share.

---

### Post by meem1029 on 2011-10-08
I have a similar setup except with Ubuntu 10.10.  What I did is made a smallish partition for windows and one for Ubuntu, and then a large partition for data.  Windows and data were ntfs, while Ubuntu was ext4.  This has worked well for me.

---

### Post by Basher101 on 2011-10-08
i got a 550 GB shared NTFS partition, Windows has 30 GB and Ubuntu 20 (16 GB + 4GB swap). I did not use any program to get it to work, i just partitioned with Gparted from the live CD, installed and it worked. Dont know why it has to be FAT 32. NTFS works just fine

---

### Post by Toz on 2011-10-08
> **Basher101 said:**
> Dont know why it has to be FAT 32. NTFS works just fine

True. Last time I tried this, writing to ntfs partitions was still problematic. I just use network shares now.

---

### Post by KurtCho on 2011-10-08
if you are willing to spend some time with gparted here is what I suggest

Shrink your ubuntu (or windows(or both)) partition. Make a partition in the empty space. Move my (your) documents into one of those new partitions, do the same with ubuntu (there are plenty of guides to doing this), voila.

If you really want ubuntu and XP to co-exist, then you can use your my documents folder as your home folder.

good luck

---

### Post by DeadlyOats on 2011-10-08
That link to those softwares that help windows access linux seem to me to be a new back door for hackers and crackers to violate linux via windows.  Or am I being too paranoid?

You're logged on to windows, and a malicious software makes its way into your windows setup, then BAM!  It has access to your linux partition as well because of that software.  Am I being too paranoid, or is it something that really needs to be guarded against?

---

### Post by [S|G] on 2011-10-08
> **DeadlyOats said:**
> That link to those softwares that help windows access linux seem to me to be a new back door for hackers and crackers to violate linux via windows.  Or am I being too paranoid?

Only if the Windows system has been compromised in first place. If someone had access to the windows system they'd be able to see the files on the linux disk. Anyway, AFAIK there is no functional tool to access EXT4 drivers with read/write access.

I found that having a small Windows partition + small Linux partition + big shared NTFS partition for data works best for me while sharing files between the two systems.

---

