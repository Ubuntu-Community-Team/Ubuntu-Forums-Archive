---
title: "I Deleted My Windows Partition"
date: 2010-05-31
forum: General Help
---

### Post by hitmen on 2010-05-31
I am actually backtrack (type of Ubuntu)

Aim: To create a bootable Backtrack USB device
Result: I think I erased my Windows files
Now it cant even boot without a thumbdrive.

What I did:
#delete existing partitions. How do I check if I deleted the partition on the thumbdrive or harddisk?

create two partitions with the first being 1500MB.
set the first partition to vfat and the second is blank.

This is the result:

/dev/sda1 fat32 size: 1.47GiB Used 2.96MiB Unused: 1.47GiB Flag:Boot

/dev/sda2 ext3 Size: 231.41GiB Used: 3.82GiB Unused: 227.60GiB

/dev/sb1 Size: 3.73GiB Error: Cant open /dev/sdb1 No such file or directory. Cannot initialise H: 
Mlabel: Cannot initialise drive.

There is something very very wrong with my partitioning:

1)I wanted to format the thumbdrive but how did it wipe out the harddrive!!???

2)I cant boot my primary hard disk (Windows). What should I do?

3) Why is there an extra i in GiB instead of GB?

4) Why is my entire harddisk in /dev?? I thought dev is only for devices.

5) How do I boot my Windows again? My BIOS says it is not bootable. 

Please **[SIZE="7"][SIZE="5"]help[/SIZE][/SIZE]**!!!! I am pulling my hair out.

---

### Post by Ozymandias_117 on 2010-05-31
> **hitmen said:**
> I am actually backtrack (type of Ubuntu)

Aim: To create a bootable Backtrack USB device
Result: I think I erased my Windows files
Now it cant even boot without a thumbdrive.

What I did:
#delete existing partitions. How do I check if I deleted the partition on the thumbdrive or harddisk?

create two partitions with the first being 1500MB.
set the first partition to vfat and the second is blank.

This is the result:

/dev/sda1 fat32 size: 1.47GiB Used 2.96MiB Unused: 1.47GiB Flag:Boot

/dev/sda2 ext3 Size: 231.41GiB Used: 3.82GiB Unused: 227.60GiB

/dev/sb1 Size: 3.73GiB Error: Cant open /dev/sdb1 No such file or directory. Cannot initialise H: 
Mlabel: Cannot initialise drive.

There is something very very wrong with my partitioning:

1)I wanted to format the thumbdrive but how did it wipe out the harddrive!!???

2)I cant boot my primary hard disk (Windows). What should I do?

3) Why is there an extra i in GiB instead of GB?

4) Why is my entire harddisk in /dev?? I thought dev is only for devices.

5) How do I boot my Windows again? My BIOS says it is not bootable. 

Please **[SIZE="7"][SIZE="5"]help[/SIZE][/SIZE]**!!!! I am pulling my hair out.

1. Well, I don't know HOW you partitioned, but you could have selected the wrong /dev/sd*

2. Boot to a LiveCD and post the results of ```
sudo fdisk -l
```

3. Because technically, that is the correct way of presenting it (GiB would be 1024 gigs where GB would be 1000 gigs, most people/programs just use GB for both)

4. Your hard drive IS a device... Just like how your monitor, speakers, printer etc is in /dev

5. If you really did wipe the partition, you may have to reinstall.

---

### Post by dtfinch on 2010-05-31
If it actually reformatted after repartitioning, which looks likely, then I don't think you have a lot of options (see 2nd paragraph). If it didn't reformat, you could repartition it back to what it was before if you can remember.

If you have a second hard drive handy, you might be able to recover some files, with a tool that scans for headers of specific types, but you won't know their original names and folders. Some tools (like foremost and magicrescue) are mentioned at [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) , but I've never had to use them.

---

### Post by ipatfrmww on 2010-05-31
1) what program were you doing the partitioning from?

4)everything in linux is a file. things in /dev are in files called block devices. these are essentially the devices in the computer. for example /dev/sda would be your hard drive(normally). sdb would be a second hard drive or whatever (depends).
consequently /dev/sda1 is a partition on sda. as is sda2. When you see files the file system its cause you have mounted a partition. For example, I have an NTFS partition which i use as common files for winblows and linux. This is at sda5. When it is mounted it becomes a folder at /media/data
So the short answer is that its cause your hard drive IS a device.

- have you noticed that your sda is 250gb, that means it IS your hardrive, and that means your stuffed cause windows wont fit into 5gb, which means it aint there no more

---

