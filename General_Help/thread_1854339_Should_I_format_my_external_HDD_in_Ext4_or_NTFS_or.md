---
title: "Should I format my external HDD in Ext4 or NTFS or other?"
date: 2011-10-04
forum: General Help
---

### Post by Rytron on 2011-10-04
Hi.

Should I format my external HDD in Ext4 or NTFS or other?

I have GNU/Linux installed on both my Desktop and Laptop computers.

What are the advantages/disadvantages?

I'd appreciate any advice on this.

Thanks.

---

### Post by dino99 on 2011-10-04
if your systems/machines are all using linux then ext3/ext4 is the secured choice. If this external will be used and plugged on other non linux OS, then ntfs is widely readable/writable directly or by adding codec, but ext3 is fully supported by windoz too.

---

### Post by binary00mind on 2011-10-04
[FONT="Trebuchet MS"]If you only use Linux OS's it doesn't really matter. If you use Windows then use NTFS. 
Even if you don't use Windows, there is always that remote chance that you may need to hook up to the Computer with Windows, then you have access to all your files. 
Also it depends if you use encryption on your Linux, if yes, then go with Ext4 or divide the whole disk into two partitions, one with NTFS/FAT and the other with Ext4
Note: FAT32 does not have security streams so if you open a file in Windows all permissions are set to "everyone" and you cannot manipulate with them[/FONT]

---

### Post by 3Miro on 2011-10-04
I use Linux exclusively on all of my machines, however, I partitioned my external HDD with both an ext4 and NTFS partitions. Every now and then I have to move files to friends' Mac or Windows machines, so I use the NTFS.

---

### Post by elliotn on 2011-10-04
I would format it as NTFS as u may need it when copying staff from friends who don't use Linux

---

### Post by collisionystm on 2011-10-04
I would use FAT32.

You can force a format of FAT32 on a large partition. I did it with my 1tb drive so I could use it with my PS3 lol.

---

### Post by coldraven on 2011-10-04
FAT 32 has a 4GB file size limit so it's no good for DVDs.
Last week I had to format my 8GB memory stick to NTFS for that reason.
I use NTFS on my 1TB external drive so that I can take it to my friends' houses and plug into Mac or Windows.

---

### Post by oldfred on 2011-10-05
NTFS is better than FAT32, unless like collisionystm you have to have FAT for use with another device. But with FAT32 a chkdsk may take days on a very large drive.

If you have any windows partitions NTFS, FAT32 then be sure to have a Windows repairCD so you can run chkdsk on the partition. 

Ubuntu runs fsck every so many reboots, but cannot run a chkdsk on a Windows partition.

---

