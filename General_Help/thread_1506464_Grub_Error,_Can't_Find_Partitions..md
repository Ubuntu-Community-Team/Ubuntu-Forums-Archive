---
title: "Grub Error, Can't Find Partitions."
date: 2010-06-10
forum: General Help
---

### Post by Raditude on 2010-06-10
Hello,

I have a 320GB Hard Drive, divided into 4 partitions.

20GB   Windows 7 Home Premium x64(NTFS)
20GB   Mac OSX Leopard
20GB   Ubuntu 9.10 x64 Root (Ext4)
260GB Ubuntu Home (Also used for File Share with Windows and Mac) (Ext2)

I'm using [Ext2FSD]("http://www.ext2fsd.com/") for Windows to allow it to view the Linux Partition, and another program on Mac so it can view the Linux partition.

Yesterday, I was having trouble getting Windows to recognize the 260GB Partition. It had worked for awhile, allowing me to save my files to it, but now it wanted me to format the partition before I could use it.

I think I accidentally changed a setting in Ext2FSD, which screwed up the computer.

When I rebooted, Grub came up saying it couldn't find the selected partition, and had a command prompt that said Grub Rescue.

I booted into the Ubntu Live CD, so I could just reinstall Ubuntu, which would also reinstall Grub. When I did that, it said the Hard Drive was completely empty and unallocated. I restarted on the Live CD, and opened Disk Utility. It shows the Windows Partition and the Mac Partition, and I have access to the files. Both the Linux Partition, and the File Share were unallocated though.

I opened up GParted, and tried to partition the space, but it said the Hard Drive was completely empty, again not showing my Windows, or Mac Partitions.

I don't want to have to reinstall everything again. I have reinstalled and activated Windows several times in the last few weeks, that I had to call Microsoft to activate it the last time. It is a legit copy.

What can I do?

---

### Post by dabl on 2010-06-10
> **Raditude said:**
> 

I think I accidentally changed a setting in Ext2FSD, which screwed up the computer.

...

I opened up GParted, and tried to partition the space, but it said the Hard Drive was completely empty, again not showing my Windows, or Mac Partitions.



I think you accidentally overwrote the partition table on the MBR, somehow -- that's a very bad thing.  I hope you have a backup of your data -- this may or may not be a recoverable situation.

I would start with making a Super Grub Disk, and start making like a student of data recovery: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If you are able to find valid partition information and mount the partition where your data are, then you need to copy it off to somewhere safe.  I suspect you are going to have to make a new partition table and repartition that hard drive before you'll be able to install an OS on it and use it again.  :-({|=

---

### Post by oldfred on 2010-06-10
I have not used it but sometimes testdisk will see the partitions.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

I always suggest a shared NTFS partition for data you want to share between systems or if all linux a shared /data partition. Even some windows users suggest a separate data partition so when windows breaks you can reinstall without loss. I consider /home part of the system so I would not want other systems writing into it. Just as I do not write into my windows system partition unless it is for repairs.

---

### Post by Raditude on 2010-06-11
The computer completely crashed on me now. It wouldn't boot past the POST. It turned out that my Hard Drive was bad, and I have to send it in to Acer to have it repaired or replaced.

Thanks anyway for the help.

---

