---
title: "Which File System to use? Pros and Cons"
date: 2010-02-05
forum: General Help
---

### Post by exup1000 on 2010-02-05
Hi

I would like to know which file system is most suitable for the following cases. I did a bit of a google search but the results were returning some rather detailed information of the types.

I have a number of drives and wondered which is the most suitable.

Removable back up drive (written once a week and then removed) 1TB
Primary drive which I assume is where the swap file is and system files 320GB
Seconday drive where all my day to day files are kept.320GB
Some more secondary drives 320GB for VM images and I could dedicate one to just being the swap file location if that is noticeable speed improvement.

If anyone know of a good article showing in brief the pros and cons of each file type that would be great.

Also I do have some windows clients that connect to the drives. So I may be limited to just NTFS?

Option I can select are EXT2,3,4 XFS FAT, SWAP and NTFS

Cheers

---

### Post by audiomick on 2010-02-05
Here's a link to the documentation:
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
and another one about partitioning.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You don't have to give your swap partition a whole drive. Rule of thumb is a bit bigger than your ram if you want to hibernate. If you don't, maybe a GB or so, unless you are planning on editing 3 feature films simultaneously or whatever. I have 4GB of RAM, and practically never get into the swap.

As far as file system for you go, anything that needs to be accessed by windows will have to be NTFS. Otherwise, I would go with Ext4. There were a couple of problems with it when it first came out, I believe, but I think they are sorted. The argument against Ext4 is that it has a higher overhead, i.e. uses more of the drive for itself. With the amount of drive space you are talking about, I don't think that is an issue.

By the way: how do you make something impossible to buy?
Give it a Yamaha part number...;)

---

### Post by mrkazoodle on 2010-02-05
If you want your windows systems to be able to access the drives, you can use Ext2 as well as Ext3, maybe even ext4 ([http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/))
Ext2IFS vs Ext2fsd: drivers to mount Ext2/Ext3 file systems. Ext2fsd has been proven to be able to mount Ext4 drives with extent disabled (described in tutorial), but it is heard that it could even work with extent enabled (did not test this myself). Ext2IFS can not mount standard configured Ext4 partitions, the inode size on Ext4 is by default set to 256 which is more than it can handle. I don't know if you can change the inode size and I'd doubt it being worth knowing.
I haven't tried it yet, but I would go for ext4. (it's the fastest)

About swap: this is what linux uses when it runs out of RAM or as audiomick said, whey hybernating. So it doesn't affect speed directly.

---

### Post by Yellow Pasque on 2010-02-05
XFS, NTFS, FAT? No. If you have Windows clients, use samba.

Removable back up drive (written once a week and then removed) 1TB
EXT3

Primary drive which I assume is where the swap file is and system files 320GB
EXT4

Seconday drive where all my day to day files are kept.320GB
EXT3

Some more secondary drives 320GB for VM images
EXT4

---

### Post by exup1000 on 2010-02-06
Hi many thanks for all the information. I read through the tutorial links and they made sense.

So have opted to go for ext4 for all of them.

Cheers Exup

Any yes Yamaha part numbers do make sense.

---

### Post by mushwars on 2010-02-06
take a look at this thread. it is sticky in the installing forum.

[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

---

