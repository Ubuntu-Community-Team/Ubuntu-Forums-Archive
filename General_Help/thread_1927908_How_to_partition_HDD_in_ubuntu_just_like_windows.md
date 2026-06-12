---
title: "How to partition HDD in ubuntu just like windows"
date: 2012-02-19
forum: General Help
---

### Post by suryak on 2012-02-19
Hi,

I have previously used Ubuntu for a year and seriously faced trouble in storing/ sorting my data. 

When I use Windows, I would partition it into 4 drives so that I would install Windows in one partition and store my personal/work data in other 3 drives. (one drive for music, videos; one drive for work; one drive for documents; I leave the OS installed drive for installing software's)

Thus, when I had to re install OS, my data wouldn't go anywhere.

However, when it comes to Linux, we have a different architecture where locations are branched from "/" (/home; /home/usr; /home/etc; these branches may not be correct exactly. but this is how it looks).

I don't even have a "my computer" option from where I can go to my created partition, I find a bit hard to sync with Linux... 

So, I wonder if you could help me in this. How should I partition and what locations I should use for mounting?.

# I don't remember exactly but, I used /home/usr as one mounting location for a partition when I used Ubuntu. When I opened it, I was surprised looking at that location which had many files already installed. (I had serious trouble in sorting my data).

Anyone from windows OS would understand my trouble clearly.

---

### Post by athampan on 2012-02-19
@suryak In Linux, permissions play an important role.   The directory structures in Linux are designed with that in mind and needs a paradigm shift in thinking. 

What you mention as different partitions for different purposes, can be easily achieved by using different folders within your home directory.

If  you still need those partitions, then you will need to partitition your drive prior to linux install (i.e. if you want 4 different partitions, you can use the live CD for linux and use the program call gparted to create the partitions).  But if I wouldn't know the structure of linux, I would be careful in doing this (or would completely avoid doing this and go with a default install) until I become more familiar with the linux landscape.

---

### Post by suryak on 2012-02-19
Well, creating folders in /home instead of drives is a option but I rather try to avoid it if I had got a better option.

regarding partitioning:

I could create partitions while installing or using gparted at terminal. My question is, I should be mounting those partitions to /usr; /etc; any other...

I agree that I need to sync with Linux things.. But is there any "My Computer" kind of option that would show all mounted drives just like that of windows??


I hope you have understood my trouble. I might have not expressed in good way but please try to give the best solution on it..

Thanks

---

### Post by suryak on 2012-02-19
As you mentioned, I didn't know that each mounting location has a particular purpose. Would you like to mention a few in brief.

#Please mention a good partition table for me which solves my purpose
Currently I am using Win7. So I divided it into 3 partitions (c,d,e). C contains OS. I use other 2 drives for storing my data.

So, if I had to re install OS, I don't have to worry about data backup which is present in other drives.

This is what I am even looking in Linux.

So, how do I partition and mount locations..

For example if I didn't partition and used the whole disk as a whole and mounted at /home. My data will be lost if I re-install my OS.

---

### Post by larrypg on 2012-02-19
Hello,

First a quick question...are you going to be installing Ubuntu to your Windows drive?  It seems you have four partitons already.

---

### Post by nothingspecial on 2012-02-19
Are you creating a partition table from scratch or do you want to know how to mount existing partitions to specific places?

---

### Post by athampan on 2012-02-19
@suryak you have two options 

(a) install linux using the windows ubuntu installer (wubi) which should install the linux into your windows (so you won't have to do any partition changes)

(b) use something like easeus and shrink the partition on which your windows is installed (and then format the extra space on your drive to ext4 ... that way the live CD will find the partition to which it needs to install and all your /usr and /home etc. will be living on this partition and you won't have to mount it separately and neither will you lose any data).  

The nearest equivalent that I can think of for "My Computer" is under the Places (that will show you all the mounted partitions and disks) showing up on the top left of your toolbar (if you use gnome classic window manager) - it also has a Computer option within it that shows the disks that are on the computer. If you use option (b) above, you should (in principle) be seeing all your partitions within the Places tab.

Hope this addresses your doubts.

---

### Post by suryak on 2012-02-19
Thanks for your comments but no one got my point. let me explain again
1. My worry is not about how to install it, its about how to maintain it.

Let us assume a Win7 OS System containing 4 partitions (c,d,e,f). C consists OS. If I had to format my OS, I would simply do C and still my data on other drives would be safe.

In the same way how do I do it in Linux ?

- when I partition my disk during installation, I should be mounting them to some locations (/; /home; /usr; /etc; .... etc). So, all these would come under "/" aka root. If I had to delete my root partition, will the data on other partitions be safe??

Well, I just read about filesystem in linux that each mounting location has some particular significance which are meant to use for respective purposes. So, what locations I can use for mounting (I would like to place my work, music, movies, doc in separate partitions.) How would I do it in linux.

---

### Post by The Cog on 2012-02-19
I don't recommend option (a). This installs linux onto a single virtual disk located inthe windows partition whic is not at all what suryak is looking for.

Googling for "linux file system layout" gets lots of good links. But I would make a few points:

First: Linux does not use drive letters. You "mount" extra drives or partitions by joining their contents into the one-and-only directory tree. The contents of the mounted partition replace (hide) any existing contents in the directory (called the mount point) where the partition is mounted to. So looking at the directory tree (in the right branches) will show you the contents of the mounted drives. 

Second, /home/username is where you should be putting everything. It's normally difficult to place files elsewhere, and for good reason. Get used to the idea that /home/yourUserName is where you should stay (except when you are doing system administration). Get used to this, don't fight it.

Third: Combining first and second points, it is common to place /home on a separate partition to the other stuff, so that the system can be completely reinstalled without wiping the user's data and settings. Re-format the root partition, reinstall, and re-mount the real user stuff in /home when you're happy the new install works. In windows, I think people often use C: and D: in a similar way.

If you want more than one partition for user data, perhaps the best way is to mount the extra drives under /mnt, for instance /mnt/music. If this is to be mounted every time the system boots, you will need to create an entry in the file /etc/fstab to tell the system where to mount it. The entry will look much like the entry you will find there for /home. You can make a symbolic link from your home folder to /mnt/music so that you see a directory for it in your home folder if you like.

You could of course just mount the music partition directly into /home/yourUsername/music, but I don't like that idea for some reason - it just feels wrong to me.

---

### Post by nothingspecial on 2012-02-19
In linux you can mount them where ever you like.

You can mount your Videos partition to your Videos folder if you like.

Yes, you can reinstall Ubuntu to the "OS" partition without effecting data on the others.

I wouldn't worry about a seperate /usr partition or /etc partition. If you just have personal data on the other partitions you can sort out where to mount them after you install.

---

### Post by suryak on 2012-02-19
Thanks a lot, the above two threads are really helpful.

---

### Post by jingaling on 2012-02-19
Hi,

I'm not an Ubuntu expert but I do understand the file system structure, I am a Windows expert however so maybe I can add some value to this thread.

Firstly, why do you have 4 partitions on your Windows install? This isn't really needed and seems a bit of a waste, just means more partitions to defrag if you ask me. If the disk ever fails then the likelihood is that all partitions on the drive will be lost anyway so there is no real advantage to the 3 partition.

Plus there is a limit of 4 primary partitions on a disk so you need to be aware of this also and look at creating logical/extended partitions. If it was me, here is how I would partition my disk to achieve your aim:

**Windows:**
OS (C) - 20GB minimum - NTFS

Personal/Work Data - However big you want it to be - NTFS (you could create a separate work partition but I don't see the point, folders should be enough.

**Ubuntu:**
OS (/) - 20GB minimum - Ext4

SWAP - Depending on how much RAM you have changes the size of this. Some people think that if you have more than 4GB RAM then you don't need SWAP. I personally have 3GB of RAM in my machine and have NEVER used SWAP. TO be safe maybe create a 2GB SWAP just in case.

Data (/home)- As big as you like - Ext4

Boot (/boot) - 100MB - Ext4 - This will mean that your boot loader (GRUB) will be on a separate partition so if you ever remove Ubuntu from your drive, you will still be able to boot Windows as GRUB supersedes the Windows MBR.

As I said, this is just my humble opinion as to how I would partition a drive. You can of course change or completely ignore this however you like. Hope it gives you something to go off though.

Kev

---

### Post by oldfred on 2012-02-19
I do not think most desktops need a separate /boot. Old systems with a BIOS boot limit of  137GB need a /boot  partition fully in the first 137GB, also servers or server like configurations with RAID or LVM may need a /boot.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

For most new users a separate /home for data works and you can reinstall your entire system and reuse/remount th existing /home without reformating as part of the new install.

But /home has two parts. It has all the user setting and some default files/folders for programs in hidden folders and all your data in folders like Music, Documents etc. You can split /home into your user setting and then put all your data into other partition(s) or other drives.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

---

### Post by jingaling on 2012-02-19
Like I said, it's my personal opinion on the matter. I personally like to have a /boot partition so if I ever remove Ubuntu I can still boot into Windows without doing a GRUB repair. It's just simpler that way. But hey, each to their own right? :)

Kev.

---

### Post by suryak on 2012-02-19
Thanks for the information.. Its really helpful.

---

### Post by suryak on 2012-02-19
Actually, the more number of partitions increase better grouping of data and better arrangement. If I had only one partition, more number of folders and sub-folders and sub-sub-folders increase which looks very complex to use data. 

And in linux where we interact with terminal frequently to enter dir, it really sucks.

---

