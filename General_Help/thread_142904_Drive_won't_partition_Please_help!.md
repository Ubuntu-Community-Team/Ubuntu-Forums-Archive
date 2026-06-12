---
title: "Drive won't partition??? Please help!"
date: 2006-03-11
forum: General Help
---

### Post by totallylost on 2006-03-11
Ok, im a complete noob with linux (i know isnt it a shame?) and im trying to install kubuntu.  
I can get the installer to run and the network setup but for whatever reason i cant seem to partition my 200gb ide harddrive into a 150gb partition for windows and a 50gb partition for linux.  i can type in the new 150gb value but when it goes to change it i dont see anything except the blue background and then the original manual partition page comes back up with the same 200gb size value and no new partition.  What is the deal? Can anyone suggest an alternative route for me to use to get linux and xp to reside on the same drive but without ruining my xp files?  Id really like to get kubuntu installed and running. 

any help would be greatly appreciated.

---

### Post by munga_bill on 2006-03-11
It sounds like you may not have defragged enough. There's probably some Windows data in the way the Ubuntu partitioner doesn't want to interfere with. WIndows leaves its files lying around scattered all over the place like a messy kid. You have to make it clean up it's toys. Here's a good link how to do that: [http://www.geekgirls.com/windows_defrag.htm](http://www.geekgirls.com/windows_defrag.htm) Defragging consolidates your Windows files towards the beginning of the drive so the Ubuntu partitioner can do its job.
Sometimes WIndows needs a heck of a lot of defragging before it is all neat and tidy, it can take several repeated operations, like all day or all night. (Aren't you glad you are getting Ubuntu - you will soon be free from all those silly problems)!
Another thing, make sure you are typing 'GB' in after the number, or it will think you mean 'MB', and that would be too small, so it won't do anything, that's something else that it could be. Regards, munga_bill

---

### Post by totallylost on 2006-03-11
I defragged it over and over again but there is still a little bit of xp files from scandisk that didnt go to the front of the drive no matter what. any suggestions? i really want to get kubuntu on my system and this stupid install over.

---

### Post by munga_bill on 2006-03-11
Okay then, use GParted on its own LiveCd, download the latest one as an .iso file and burn it to a disk. It will even fit on one of  those small size CDs the same (physical) size as a floppy disk. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It has tools to resize NTFS or FAT partition at will defrag it for you first as necessary. That should fix it! Regards, munga_bill

---

### Post by totallylost on 2006-03-11
so i burn the live version to a cd and then reboot with the disk in my drive?
or will the disk run on windows xp?
will that make the changes permanent then as well?

---

### Post by munga_bill on 2006-03-11
Yes, you download the .iso file, and then burn it to disk as an .iso, (not as data), and you put the disk in your CD drawer and re-boot your computer with it in. It is a 'live cd' with its own linux kernel, so it's an operating system of its own that runs from your CD drive rather than from your hard disk. It can make changes to your hard disk better that way. It doesn't need Windows or any help from any other operating system. And yes, it will change your disk for you. You can call them 'permanent', (for now), but really you can always use GParted again someday if you want and make everything back the same way you had it before if you decide to. Nothing is really that permanent. Relatively permanent though, yes.

---

### Post by totallylost on 2006-03-11
alright then. im off to attempt the partitioning
thanks once again
ill let you know how it goes.

---

### Post by totallylost on 2006-03-11
alright im about to toss the hat in...
i tried gparted and it worked fine until i actually wanted to write the partitions to disk
then i got an error message saying that i had physical damage to the disk- and told me to try to fix it
so i did

but nothing happened at all and i tried it again and it still didnt work
the only way ill get linux on my computer now is to totally erase windows

gah this is frustrating!!!

im debating whether or not to install linux and then reinstall windows after that-- could i make a partition with the windows xp install disk?? and keep linux on its own then?

i dont know but basically im fed up with the linux world right now for being so darned complicated.

they say they gave up graphical interface for speed--however im seriously doubting that its any faster- ive been at this two days now almost non-stop and i dont even have anything installed whatsoever

tell me that isnt wrong

i really want this to work out but the more i try the less things seem to work

---

### Post by Mr X on 2006-03-11
[QUOTE=totallylost]Ok, im a complete noob with linux (i know isnt it a shame?) and im trying to install kubuntu.  
I can get the installer to run and the network setup but for whatever reason i cant seem to partition my 200gb ide harddrive into a 150gb partition for windows and a 50gb partition for linux.  i can type in the new 150gb value but when it goes to change it i dont see anything except the blue background and then the original manual partition page comes back up with the same 200gb size value and no new partition.  What is the deal? Can anyone suggest an alternative route for me to use to get linux and xp to reside on the same drive but without ruining my xp files?  Id really like to get kubuntu installed and running. 

any help would be greatly appreciated.[/QUOTE]
I had sort of the same problem. A search on google cleared it up!

---

### Post by Jucato on 2006-03-11
Please don't give up yet, at least not on Linux. Remember that Ubuntu is just one Linux distribution. There are others out there that might suit your system better. Have a try at the Knoppix distro or SimplyMEPIS. I heard they have good hardware detection. They are Live CD's that will allow you to also install it on your system.

Now back to your problem. I presume that you have XP installed on your system already right? During the installation, are you actually resizing the Windows partition or making a new one? I think that the problem might be that the partition utility (parted) is having a hard time resizing the XP partition.

Another theory might be that the drive is really physically damaged. I sure hope not. But I find that XP's ability to detect physical damages on storage media to be very low. (I actually find it surprising that it's able to run, sometimes, on unstable hard drives). 

Anyway, I'm not an expert on resizing partitions (I always prefer backing up and starting from scrath). You might find some help in the HOWTO sections or even in the Absolute Beginner Talk. This isn't a Kubuntu/KDE problem, but more of a general partitioning/media issue. I encourage you to keep on trying, even to try other distros that might be better for you. Linux is a wonderful world. You'll love it, once you get settled. :D

---

### Post by Princey on 2006-03-12
[QUOTE=totallylost]alright im about to toss the hat in...
i tried gparted and it worked fine until i actually wanted to write the partitions to disk
then i got an error message saying that i had physical damage to the disk- and told me to try to fix it
so i did

but nothing happened at all and i tried it again and it still didnt work
the only way ill get linux on my computer now is to totally erase windows

gah this is frustrating!!!

im debating whether or not to install linux and then reinstall windows after that-- could i make a partition with the windows xp install disk?? and keep linux on its own then?

i dont know but basically im fed up with the linux world right now for being so darned complicated.

they say they gave up graphical interface for speed--however im seriously doubting that its any faster- ive been at this two days now almost non-stop and i dont even have anything installed whatsoever

tell me that isnt wrong

i really want this to work out but the more i try the less things seem to work[/QUOTE]


Assuming that your harddrive isn't physically damaged, try using one of these to resize your partition then insert the kubuntu disk to install. Here are a few links:

[http://prdownloads.sourceforge.net/ranish/partition-manager-2.37.zip]("http://prdownloads.sourceforge.net/ranish/partition-manager-2.37.zip")

Give it another go. Oh, by the way, it's freeware released under GPL liscence.

---

### Post by totallylost on 2006-03-12
Alright this is my question.
I cant partition using that ranish thing because i dont have a floppy drive and i think that it is only good for systems up to win. 2k
ive already got windows xp installed but im debating on whether or not to just reinstall it fully and use the partition maker you get with xp setup.
would this create the partitions linux would need?
could i just reinstall windows (entirely-not just a repair) use its partition maker and create a 41gb freespace for linux and a 145gb space for windows xp? would this work? or would it still not load up right?

im not giving up on kubuntu just yet.  
im not afraid to lose my files either- ive got plenty of backups

another thing would be could i just install linux on my entire drive- and then install windows xp afterwords and make it dual-boot? or would xp get greedy and format over linux?  these are things i wish to know

thanks for the help

---

### Post by Jucato on 2006-03-12
If it's not at all a hassle for you, I'd recommend just reformatting your hard drive and reinstalling Windows. This would give you a chance to find out if your hard drive really has a physical defect as the GParted LiveCD tells you. Alternatively, there's a software called Partition Magic which works like GParted but is more catered towards Windows. However, I'm not sure how it will work if you are running it on the hard drive that you will partition.

I recommend to install Windows first before Kubuntu. Windows is usually picky about where it should sit (first partition of the first hard drive in the IDE). Also, when you install Windows, it installs it's own bootloader over anything else, and it's bootloader doesn't play nice with Linux.

It also make reinstalling Kubuntu (if you ever need to) a bit easier. Of course, there are ways to make things work even if you installed Windows after Kubuntu. But to make things easier for you, I'd recommend Windows first, Linux second. Linux doesn't mind. :D

Regarding partitions, you might also want to set up a partition where you could store data that you will need to view/edit in both Windows and Linux. Plus, it's recommended that you also have a separate partition for your swap/virtual memory. In fact, if you don't have one, I think the Kubuntu installer will make one for you. So all in all, you would need at least 4 partitions:

1. Windows (NTFS)
2. Kubuntu (ext3 or reiser)
3. swap
4. a shared partition - only if you really want/need to. 

(I personally recommend creating a separate partition for your /home directory.)

I'll cut my reply here. You might have some information overload. If you have any other questions to ask, fire away! :D

---

### Post by Princey on 2006-03-12
Looks like Fenyx beat me to it. I don't use Windows partition manager however, I assume that after first backing up your data, reformatting would do just fine as it would give you a chance to see if the drive is defective. However, Windows XP setup won't just shrink partitions if you chose to reformat. You first have to delete the partition during the setup which would give you a chance of creating a new partition, hence, allowing you to chose the new partition size. For me, I use Acronis Partition Manager that boots of a CD and it works like a charm, both for my Windows machine and Kubuntu.

When you're through partioning and installing Windows, then you can run Kubuntu installation as Fenyx said as it's better to install Linux second...somehow Windows won't see anything but Windows. Best of luck. Feel free to ask if you get stuck somewhere.

---

### Post by Jucato on 2006-03-12
Word of warning, though. This happened to me, but I'm not entirely sure if this is the general case:

A FAT32 partition created by GParted was not recognized by Windows XP.

Like I said, I'm not entirely sure if this is a general case, or an isolated problem.

---

### Post by Princey on 2006-03-12
[QUOTE=Fenyx]Word of warning, though. This happened to me, but I'm not entirely sure if this is the general case:

A FAT32 partition created by GParted was not recognized by Windows XP.

Like I said, I'm not entirely sure if this is a general case, or an isolated problem.[/QUOTE]


In that case, he could easily reformat the FAT32 drive under Windows XP chosing FAT32. Linux will still recognise it.

---

### Post by totallylost on 2006-03-12
Alright here's what im going to do.

Sometime soon im going to reinstall windows (formatting the drive and creating a new windows partition as well as partitioning the drive for 40gb of space for linux.

Am i correct in assuming that i can partition my hd so that it will have a 145gb partition for windows xp and 41gb for linux- from the windows xp install disk?

That would make the drive into two partitions xp and the non-allocated one left for linux- could i just (after i install xp again) install kubuntu and have it recognize the unallocated 41gb chunk of drive for itself and then use the automatic tool in the kubuntu installer to partition that 41gb for linux correctly or would i be better off creating (manually of course) seperate partitions for swap and the /home thinger?

Could someone please explain the functions of the /home /root , swap and other possible linux partitions. im confused as to why i need so many different partitions in the 41gb of space that i hope to get when i run xp setup again and reinstall and repartition the drive.  What are the filesystems the drive partition should use?


and i would appreciate some values (in gb) for each of the seperate partitions ill need to make in the 41gb of space that i hope to get.  how big does the /home partition need to be etc...

thanks for the help- im not giving up just yet

---

### Post by Princey on 2006-03-12
> Am i correct in assuming that i can partition my hd so that it will have a 145gb partition for windows xp and 41gb for linux- from the windows xp install disk?

That would make the drive into two partitions xp and the non-allocated one left for linux- could i just (after i install xp again) install kubuntu and have it recognize the unallocated 41gb chunk of drive for itself and then use the automatic tool in the kubuntu installer to partition that 41gb for linux correctly or would i be better off creating (manually of course) seperate partitions for swap and the /home thinger?

Yes you can, but all you'd have to do is to create the partition needed for Windows XP. Kubuntu would realise the free space and give you the option to install in that free space.

> Could someone please explain the functions of the /home /root , swap and other possible linux partitions. im confused as to why i need so many different partitions in the 41gb of space that i hope to get when i run xp setup again and reinstall and repartition the drive. What are the filesystems the drive partition should use?

I'm a linux newbie myself, although I've been using Linux for over two years now. I'm more a Windows Pro than linux, but I'm getting there. With what I've learned from this forum, reading elsewhere and from TUX Magazine, I'll do my best to explain.

1. Your /home is what it says. That's your home directory. It's where your documents, files and non-root programs get install (subject to correction)

2. /root is the base directory/drive where the core of the operating system is installed. It's where the kernel resides and the one place after install you should stay away from. (Ubuntu doesn't allow you there that easy anyhow)

3. Your /swap partition is for your swap file. No matter how much memory your computer has, there's always a time where the OS (operating system) has to swap out some of the programs in memory, when you run low of memory that is, to the hard disk. You wouldn't notice that under Windows as Windows manages it itself unless you know about it and set it aside. It's called "pagefile" under windows. You must have a swap file for any operating system (stand corrected as I know little about Macs).

Hope that helps. 1GB is fine for your swap. I'd set aside 15 for root and the rest for home. That option saves you losing data during a re-install. However, you can go with just root and swap.  Home will be created on the root partition. You'd have to chose to manage your partitions to get the three options though. Good luck and welcome to the Kubuntu fold

---

### Post by Jucato on 2006-03-12
Separate partitions for some directories is not absolutely necessary (except for the swap), but some are highly recommended. Here's a rundown on some of the more important directories

/home - Princey is right. But it doesn't only store your documents, it also stores your own personal user configurations (how you setup your desktop, your applications, etc).

/root - please take note that there is a big difference between the / (root directory) and /root (root's directory). The root directory (/), as the name says, is the very root, the mother of all directories. This is the highest and most basic directory. All directories are found in the / directory. on the other hand, the /root directory is the personal directory of the root user, also known as the superuser or administrator. Think if it as the /home for the root/admin/superuser. Please take note that in Ubuntu, this user is disabled by default, for security purposes. This is one of the unique marks of Ubuntu.
A graphical representation of the directory structure would be:
```

/ 
|
|---- /home
|
|--- /root
|
|--- /boot
etc.

```
Here's a link about this discussion in the Ubuntu wikis: [https://wiki.ubuntu.com/LinuxFilesystemTreeOverview?highlight=%28system%29%7C%28file%29]("https://wiki.ubuntu.com/LinuxFilesystemTreeOverview?highlight=%28system%29%7C%28file%29")

/swap - there is actually no /swap directory. We call it a swap partition, or just swap. What Princey has said basically covers it. Ubuntu makes it a default to have a separate partition for swap, as this is the most efficient setup. There are many opinions on how big your swap partition should be depending on the amount of physical memory (RAM) that you have, but there is no set rules. Some say that it should be 1.5 times bigger than your RAM. I actually made mine about 2 times bigger. The Ubuntu installer makes a default size if you don't specify it yourself. I'm not entirely sure how big it is. 1GB would be fine.

The partition sizes Princey gave is ok. Personally, I have my root partition (which includes everything except swap and /home) at 10GB, my swap partition at 1GB (900MB+ actually, I entered 1GB in the installer, but Ubuntu adjusted the space to make room for some hidden files I guess) and the rest goes to the /home directory. Making a separate partition for the /home is for the purposes Princey mentioned. On a more basic level, it also protects your data in case the root partition gets damaged/corrupted. Same is true actually in any OS. 

The reason I recommended having a sort of shared partition (in FAT32 format) for Linux and Windows is for when you need to see some files/data/programs in both Linux and Windows. For one, Windows can not detect/read other file systems (ext2, ext3, reiser, etc), but there are programs in Windows that you can download to do this. Second, It is highly discouraged to write data on NTFS partition when you are in Linux, as there is a danger that your Windows installation might get corrupted/damaged. It's ok to read, but not to write. And by default, NTFS partitions are write-protected and only root can access them.

Hope this clarifies a few things.

---

