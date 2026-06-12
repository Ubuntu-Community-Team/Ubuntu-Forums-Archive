---
title: "Ext3 partition showin in windows as RAW"
date: 2010-03-26
forum: General Help
---

### Post by pjani on 2010-03-26
Hy i have here some weird problem. I created primary partition for Ubuntu. And for some reason that partition starts showing up in Windows XP as RAW. The partition should NOT be visible. In explorer. I tried with Ext4, Ext2 same thing, ext partitions should not be visible in windows.

Any idea?

---

### Post by ProfessionalOPs on 2010-03-26
wow ive never seen this one before.....i would try reinstalling windows because i dont think that ubuntu is the problem

---

### Post by falconindy on 2010-03-26
Why do you think that the partitions shouldn't be visible in Windows? Windows can't understand the filesystem format, but there's nothing preventing it from seeing the physical partition.

---

### Post by ProfessionalOPs on 2010-03-27
Falcanindy has a logical idea, but the fact that they appear as RAW in windows is an entirely different phenomenon.

---

### Post by Wiebelhaus on 2010-03-27
It should show RAW if your looking at it in Disk Management , Think about it [windows doesn't understand it so it assumes it's a raw partition]("http://support.microsoft.com/kb/822653").

---

### Post by ProfessionalOPs on 2010-03-27
Oh, he never stated that it was appearing as RAW in disk management, I assumed that he was infering My Computer.

---

### Post by Rocket2DMn on 2010-03-27
You need a third party driver in order to recognize and mount an ext2/3/4 drive in Windows.  Check out [http://www.fs-driver.org/](http://www.fs-driver.org/)
It will mount as an ext2 partition, so it won't use journaling, which means if it fails to write correctly to the partition, you will need to run fsck on the partition later.  I've used it with ext3 without issues, but I haven't tried with ext4.  If you don't need to read/write files on your linux partition in Windows, it is probably safer to not even mount the partition on a drive letter in Windows.  A shared partition in NTFS or FAT format is preferable to letting Windows write to the ext2/3/4 filesystem.

---

### Post by ProfessionalOPs on 2010-03-27
> **pjani said:**
> Hy i have here some weird problem.........RAW. The partition should NOT be visible. [SIZE="5"]In explorer.[/SIZE] I tried with Ext4, Ext2 same thing, ext partitions should not be visible in windows.

Any idea?

Ah yes he did mean that it appeared as RAW in My Computer as he stated "In explorer.

---

### Post by pjani on 2010-03-27
The problem is it never done this before. Windows never showed this type of partitions in explorer...I was using Ext2 IFS driver once ago, but i uninstalled it, because it was causing slow responses in explorer.

The drive letter G is not assigned to any of partitions in Disk Manager.

---

### Post by ProfessionalOPs on 2010-03-27
hmm it looks like windows has F***ed up again.....

---

### Post by lavinog on 2010-03-27
> **pjani said:**
> The problem is it never done this before. Windows never showed this type of partitions in explorer...I was using Ext2 IFS driver once ago, but i uninstalled it, because it was causing slow responses in explorer.

The drive letter G is not assigned to any of partitions in Disk Manager.

Since you installed the IFS driver, it is possible that something didn't get removed during the uninstall.

You might try installing the latest version, then uninstall and see if that works.

If it was uninstalled a long time ago, and you suddenly started getting this issue, it could have been an update to windows that triggered this.

---

### Post by pjani on 2010-03-27
Windows can produce top 5 weirdest sh** on this planet, without a reason. Now i reninstalled-uninstalled IFS driver and i have not 1, but 3 RAW partitions.

---

### Post by pjani on 2010-03-27
Problem solved. I had to uninstall ifsmount driver by hand in device manager, ext2 IFS dont completely uninstall drivers...
Now i can install ubuntu.

Thankyou for your time.

---

### Post by lavinog on 2010-03-27
> **pjani said:**
> Problem solved. I had to uninstall ifsmount driver by hand in device manager, ext2 IFS dont completely uninstall drivers...
Now i can install ubuntu.

Thankyou for your time.

How was this preventing you from installing ubuntu?

---

### Post by pjani on 2010-03-28
Some weird stuff was happening so i didnt want to dammage any other partitions data.

---

