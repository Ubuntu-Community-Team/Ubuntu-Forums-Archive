---
title: "i lost my d:drive data,what is 'lost+found' folder in ubuntu"
date: 2011-02-02
forum: General Help
---

### Post by connect2jan on 2011-02-02
hi all
in my system around 73gb(pc-desktop)
 i have1 primary partition(windows)-25gb, 1-extended partition(remaining gb)
3 logical partitions were there in one extended partition
in one of logical partition d:drive is there.i dont know i am not able see the data of d:drive
------------------------------------------------------------------------------------------------------------------------


in each logiacl partition existed 'lost+folder'(with 'x' mark),i am bit confusing with this folder
what is this 'lost+folder'(wuith 'x'mark) ,cant we remove,cant we hide,is there any problem if we remove/hide


---------------------------------------------------------------------------------------------
main problem is i have d:drive with capacity 35gb,in that i have around 32gb data,
 i lost my hole data(its not appearing),instead of this data,lost+folder came when i click this folder one dialog box is appearing with msg--ie"
"""**the folder contents could not be displayed.**You do not have the permissions necessary to view the contents of "lost+found""""
can any one plz help in this-its very imp data(which one is not appearing)
thanks in advance

---

### Post by coffeecat on 2011-02-02
A few points of information.

A partition with a lost+found folder is formatted with a Linux filesystem such as ext3 or ext4. The lost+found folder is owned by root which is why, as an ordinary user, you see a 'X' on it, and why you get the permissions error. The lost+found folder is where recovered data is placed by a filesystem checking utility such as fsck if there has been  filesystem corruption. Normally it is empty and you can safely leave it alone.

Your 'D:' drive would have been formatted with a Microsoft filesystem such as NTFS or FAT32, neither of which would have a lost+found folder. If you are finding a lost+found folder where you think the D: drive should be, you are either looking in the wrong partition or the partition has been reformatted with a Linux filesystem.

So that we can see exactly what is on your system, open a terminal and post the output of these two commands:

```
sudo fdisk -lu
sudo blkid
```Please post the output in [noparse]```
 and 
```[/noparse] tags for legibility. You can use the # icon in the message toolbar for this.

One last point. You have posted in the Testimonials section which is not for support threads. I'll ask a member of forum staff to move it for you.

---

### Post by s.fox on 2011-02-02
Thread moved to [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")

---

### Post by irv on 2011-02-02
If you want to get a graphic picture of your HD do this.
System> Administration> Gparted Partition Edit.
You will need to put in your password to display it.
Once you display it, go to Applications> Accessories> Take Screenshot. Select Grab the current window.
Once you have the screenshot, in the reply to thread just select the paper clip to attached the file to a post. We will be able to see your hard drive and how it is setup.
[ATTACH]182542[/ATTACH]   [ATTACH]182543[/ATTACH]  [ATTACH]182544[/ATTACH]

---

### Post by connect2jan on 2011-02-03
hi 
i am attaching my hard disk screen shotbelow
just see that once


that d: drive is very imp for me (i have my data)
i am not able to see this data of d:drive
------------------------------------------------------------------------------------------------------------
hi [coffeecat]("http://ubuntuforums.org/member.php?u=129087") ,i tried 2 commands (which one u posted me),just see i pasted in below the result of commands
**1st coomand:sudo fdisk -lu:**

janu@janu-desktop:~$ sudo fdisk -lu
[sudo] password for janu: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sda2        52436221   156301311    51932545+   f  W95 Ext'd (LBA)
/dev/sda5        52436223   121676309    34620043+   b  W95 FAT32
/dev/sda6       121677824   154761215    16541696   83  Linux
/dev/sda7       154763264   156301311      769024   82  Linux swap / Solaris

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037b0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7837695     3918832    b  W95 FAT32
------------------------------------------------------------------------------------------------
**2nd command:sudo blkid**

janu@janu-desktop:~$ sudo blkid
/dev/sda1: LABEL="Windows" UUID="3810B03010AFF2D4" TYPE="ntfs" 
/dev/sda5: UUID="abc30a9a-b200-442f-8448-1512a96b6326" TYPE="ext4" 
/dev/sda6: UUID="61f8236d-ad5a-4649-aa45-b143c545ac59" TYPE="ext4" 
/dev/sda7: UUID="2178dc8c-283b-4ca6-962d-0302cf909063" TYPE="swap" 
/dev/sdb1: LABEL="PENDRIVE" UUID="2C51-823A" TYPE="vfat"

---

### Post by connect2jan on 2011-02-03
hi
in my hard disk d: drive is -/dev/sda5

previosly i was fat -file system , (d:drive-/dev/sda5),
i remember i changed the (d:drive-/dev/sda5) file system to ext3,4 (in screen shot it is ext4),with following  command  using terminal

'sudo mkfs -t ext4 /dev/sda5'

after doing(changing the file system) this one ,i am facing above  problem
now i think this all clear-plz provide solution
thanku

---

### Post by coffeecat on 2011-02-03
> **connect2jan said:**
> i remember i changed the (d:drive-/dev/sda5) file system to ext3,4 (in screen shot it is ext4),with following  command  using terminal

'sudo mkfs -t ext4 /dev/sda5'

By doing that you reformatted the partition and the new filesystem has no knowledge of the data that was on it when it had a FAT filesystem. Why did you reformat it? Did you back up the data on it before you reformatted? Were you aware that reformatting a partition effectively deletes all data on it?

If you have no backup and you need the data that was on it, the only way of retrieving it is by using data recovery software. Don't try to write to the partition, otherwise you may overwrite stuff that is already there. Then you will either have to employ professional data recovery specialists - which is very expensive - or use photorec, which is not easy. Photorec comes with testdisk, which is in the Ubuntu repository.

---

### Post by connect2jan on 2011-02-04
[U][COLOR=Black][hi]("http://ubuntuforums.org/member.php?u=129087")
[ ]("http://ubuntuforums.org/member.php?u=129087")[/COLOR][coffeecat]("http://ubuntuforums.org/member.php?u=129087")[/U][COLOR=Black]_[]("http://ubuntuforums.org/member.php?u=129087")_

ya i changed the filesystem ,so am cant see the data ,
is there any option to 'undo'(to fat filesystem,by this i can see .access dat)


so plz provide solution
thanku
[/COLOR]

---

### Post by coffeecat on 2011-02-04
> **connect2jan said:**
> 
is there any option to 'undo'(to fat filesystem,by this i can see .access dat)


I very much doubt it. By reformatting to ext4, you will probably have overwritten the file allocation table of the previous FAT filesystem. Most of your files will not be overwritten though, which is why I suggested using photorec. It's been some time since I've used photorec, so I'm reluctant to guide you through it - I don't want to give wrong advice. See what I say at the end of the post.

I'm sorry that this has happened to you. This may sound harsh but is meant in a kindly way: you have learnt some valuable lessons. Specifically the importance of keeping separate backups and how imperative it is to understand terminal commands before you run them.

By the way, there is an interesting inconsistency in the terminal output of the commands I gave you to run. In post #6 you say:

> **connect2jan said:**
> 'sudo mkfs -t ext4 /dev/sda5'

... which would have reformatted sda5 as ext4. And, indeed, in post #5 your screenshot shows sda5 as ext4, as does blkid

> **connect2jan said:**
> janu@janu-desktop:~$ sudo blkid
/dev/sda1: LABEL="Windows" UUID="3810B03010AFF2D4" TYPE="ntfs" 
/dev/sda5: UUID="abc30a9a-b200-442f-8448-1512a96b6326" TYPE="ext4" 

But fdisk, which reads the partition table, tells differently:

> **connect2jan said:**
> 
/dev/sda5        52436223   121676309    34620043+   b  W95 FAT32

I'm 99.9% sure that this is because mkfs does not update the partition table - you have to run fdisk for that. I point this out because it could be confusing. It doesn't alter the fact that you have reformatted the partition. However, I will ask a couple of people to glance over the thread to see if anything else needs to be said. If not I suggest you start a new thread. Give it a meaningful title such as  'help with recovering lost files' and people with recent experience of  such things will hopefully respond. Describe what has happened in your  first post and link back to this thread so that people helping have  access to the whole story.

---

### Post by Quackers on 2011-02-04
I would agree that testdisk/photorec may be the only way to get back your data - if that is possible.

---

### Post by ricci_ritxi on 2011-08-07
coffecat
I had 4 partitions in my computer 1ntfs w7, 1 fat32 340GB, 1 wap 4,1GB, 1ext4 250GB. I had a problem with ubuntu and I reinstall it. I only resized the FAT32 to get a little more of space in the ubuntu installation, everything was all right but my fat32 partition became ext4 (even if I said do not touch in the installation process). This partition has a folder "lost+found" about 43GB (corresponds to the data stocked). When I try to open from Ubuntu, it says I have no permission. I try with : sudo nautilus and it is empty, but it still has 43GB. I have most of my data in a hard disk, and I will lost just one day of work. Can I recover the whole data form the lost+found folder?
Thanks

---

### Post by coffeecat on 2011-08-07
@ricci_ritxi, if you simply resize a FAT32 partition it cannot turn into an ext4 partition by itself. It has to be reformatted. But if the FAT32 partition had 43GB of data and was reformatted to ext4, the data would be unknown to the new filesystem and nowhere would you get the figure 43GB. And if you reformatted a FAT32 partition to ext4, the lost+found folder would be empty. So I don't really follow what you describe.

Let's do some investigation. Boot into Ubuntu, open a terminal and run this command:

```
sudo fdisk -lu
```

Post the output between [noparse]```
 and 
```[/noparse] tags. This is important - it is difficult to read otherwise.

Now mount the partition you are referring to (from the Places menu or Places sidebar of a nautilus window), and then run this command:

```
df -h
```

Post the output, again between code tags. Apart from mounting the partition, do not try to use it, and particularly do not write to it. If the worst comes to the worst you will need to use data recovery software and you must not write to that partition.

---

