---
title: "Where does it store files?"
date: 2010-09-30
forum: General Help
---

### Post by petrasflorin on 2010-09-30
OK so after all this installing Ubuntu is now warning me it has no more space.

Question: Where does it store the temp files and how do I know I can safely delete something?

I'm confused, it's like every program installs wherever it feels like it, and uninstalling it will all sorts of traces in home like the ".program" folder and other places too.

I feel like my ubuntu is getting bigger and bigger because I have no idea which folder stores what. It's so confusing, windows had C:/Program Files and that it.

Here? sudo apt-get remove , sudo apt-get autoremove
check package manager, check installed software

check all the folders
check the hidden folders in /home

I mean OH MY GOD.
I installed wine, then uninstalled it, but if I search for wine with nautilus I still find like tens of search results.

Can someone explain the "folder" tree of linux ? and also where are programs installed, where are their temp files kept, where are the shortcuts and icons kept etc..

---

### Post by searchfgold6789 on 2010-09-30
Try bleachbit. ```
sudo apt-get install bleachbit
```It worries about all that stuff for you.
Bleachbit takes up 1.5 Megabytes (1500 kilobytes) of space to install.

---

### Post by WishDasher on 2010-09-30
I can't really answer the question, but did you try apt-get remove purge(or "complete removal" in the package manager). The purge command tells it to remove configuration files, which may help.

---

### Post by swagatmishra on 2010-09-30
everytime you install a new software using apt-get or synaptic package manager,
apt stores the downloaded packages at /var/cache/apt/archives.
you can delete those archives to free up space

---

### Post by Frogs Hair on 2010-09-30
Synaptic Package Manager >  settings > preferences > files tab , check delete downloaded packages after installation . this should help a bit.

---

### Post by oldos2er on 2010-09-30
> **petrasflorin said:**
> Can someone explain the "folder" tree of linux ? and also where are programs installed, where are their temp files kept, where are the shortcuts and icons kept etc..

/tmp should be cleared on each boot.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

How much space did you give your Ubuntu installation?

---

### Post by petrasflorin on 2010-10-01
Thank you for all of your answers.
Keep them coming please :).
@oldos2er: 20 gigs.

---

### Post by petrasflorin on 2010-10-01
BTW: another question so I don't create one more topic, about the same thing, files and files.

So let's say I decide to install only Linux on my machine.
I have a 1TB WD Caviar HDD.
So, I make a "/" partition a swap partition and then... all the rest to /home ?!

The thing is: I will be reinstalling lots of linux versions and reinstalling ubuntu alot, and in windoze I was used to C:/ and D:/

I only formatted C:/ and kept D:.

That's what I wanna do in linux too. I know, don't format /home.
but the thing is I want to format home cuz there will be loads of crap that I don't want/need anymore there too.

Question: What can I do to have an extra partition to /home in which I can formatproof store files like Movies and Music and Photos that will always be there no matter what I format as long as I don't format this certain partition. For example can I create a separate partition for a folder already created by linux that I can access all the time to deposit/delete files ?

I hope you understand what I meant above... thanks.

---

### Post by SlugSlug on 2010-10-01
> **petrasflorin said:**
> BTW: another question so I don't create one more topic, about the same thing, files and files.

So let's say I decide to install only Linux on my machine.
I have a 1TB WD Caviar HDD.
So, I make a "/" partition a swap partition and then... all the rest to /home ?!

The thing is: I will be reinstalling lots of linux versions and reinstalling ubuntu alot, and in windoze I was used to C:/ and D:/

I only formatted C:/ and kept D:.

That's what I wanna do in linux too. I know, don't format /home.
but the thing is I want to format home cuz there will be loads of crap that I don't want/need anymore there too.

Question: What can I do to have an extra partition to /home in which I can formatproof store files like Movies and Music and Photos that will always be there no matter what I format as long as I don't format this certain partition. For example can I create a separate partition for a folder already created by linux that I can access all the time to deposit/delete files ?

I hope you understand what I meant above... thanks.


I alwasy keep /home unformatted -- some times rename my username to .old before reinstall then copy back what I want and leave what I dont.

I also have a /home/shared that never gets formatted

---

### Post by Silent Warrior on 2010-10-01
petrasflorin: To clarify what SlugSlug suggested, you can have a separate partition and set its mount-point to somewhere inside /home - like /home/shared (use whatever name you like instead of 'shared' if you wish).
Did you perhaps install several different *-dev-packages? Desktop environments? Tons and tons of games? Game-data and source-code take up so much space it's not even funny sometimes...

---

### Post by plucky on 2010-10-01
> Question: What can I do to have an extra partition to /home in which I can formatproof store files like Movies and Music and Photos that will always be there no matter what I format as long as I don't format this certain partition. For example can I create a separate partition for a folder already created by linux that I can access all the time to deposit/delete files ?


See [Mounting Linux Partitions in Ubuntu](http://www.psychocats.net/ubuntu/mountlinux) tutorial on [Psychocats Website](http://www.psychocats.net/ubuntu/index.php).

Good Luck

---

### Post by jgeralnik on 2010-10-01
The file system starts at the root. That is the folder "/". Everything on your system is in some subdirectory of /. Unlike windows, where you have C: and D: partitions that are not connected one to another, in unix you can have folders whose contents are on a completely different drive than their subfolders. 

For example, I can have two hard drives one of which stores my /home folder and the other of which stores my /home/Downloads folder. The most common example is mounting hard drives where all the information can be accessed at /media/sda2. The contents of /media are saved on my computer and /media/sda2 on my external hard drive.

With that understanding, you can create many partitions that you can format however you wish and all you have to do is maintain the links between your folders.

---

### Post by petrasflorin on 2010-10-05
so to understand this correctly:

I can rename my name to .old and not format home but instead copy what I want from the .old into the new name and then just... delete the .old - basically this is a quick format inside linux (somewhat).

and

I can mount any folder with any name as a separate partition inside the /home partition ? and if I format the /home partition won't that format too ?

I just... don't understand very well how linux works... I'm starting to get a grasp of it now... basically... a folder can be a partition but SHOW up in another partition... like the /shared folder. it's a partition but it looks like a normal folder under /home/name/ - did I got this things right ?

---

### Post by belkinsa on 2010-10-05
Sorry for being late but, you can use Ubuntu Tweak to clean up.

---

### Post by cpmman on 2010-10-05
> **mechafish said:**
> sorry for being late but, you can use ubuntu tweak to clean up.

+1

and Synaptic Package Manager will tell you where all your installed programs files are located.

---

### Post by petrasflorin on 2010-10-10
During install, in the partition creation menu, I used one partition mounted on / , one partition mounted on /home and created another one which I wrote in the input box to mount in /data (this is meant to deposit files in case of a reformat of everything I don't format that one).

The question is: In my filesystems, now appears a "data" folder, it's 345 GB large (I don't get it I made it 400 gigs, and this happened to all my partitions, they are considerably smaller, WTH?) is that my partition ? If so, why does it appear under the / partition ? shouldn't it be a partition by itself ? if I now format the / partition will it be formated too ?

---

### Post by petrasflorin on 2010-10-10
Anyone that has the time and knowledge to respond to my last question ? Would be greatly appreciated.

---

### Post by JKyleOKC on 2010-10-10
> **petrasflorin said:**
> Anyone that has the time and knowledge to respond to my last question ? Would be greatly appreciated.Well, I'll try. In Windows, you may have had both C: and D: on the same physical drive, but logically they were completely separate drives. Back on Win98 I usually split an 80-GB drive up into four 20-GB logical drives.

In Linux, the "/" root filesystem is **logically** similar in some ways to the physical drive in Windows. It's the container for all of the directories on the system. The key point here is that it's a filesystem rather than a partition. Every directory in the system has to trace its ancestry back to the root, but any directory can be physically located on a different drive. What ties the filesystem hierarchy and the device (drive) hierarchy together is the "mount point" and that is, in itself, a directory within the root filesystem.

If this sounds like you'll meet yourself coming back, you're beginning to get the idea. In all Unix-like systems, everything is a "file" and this includes disk drives, printers, keyboards, and the monitor, as well as actual logical files. Files are collected into directories, and directories form a hierarchy that descends from the "/" root.

The physical device "files" are all collected into a directory named "/dev" that descends directly from "/" (the "/" at the front of its name indicates that). They follow naming conventions such as "tty" for the keyboard/monitor combination, and "sda" or "hda" for SCSI or IDE hard disks. Programs reference the devices as "/dev/sda1" for the first actual partition on the first SCSI drive (although we now use the SD* name for all hard drives, not just SCSI).

"Mount points" are special directories that serve to connect the logical directory (folder) structure to the proper physical devices. Think of them as serving the same purpose as Windows' shortcuts. In Ubuntu, the conventional mount points are all put in either /media or /mnt, as subdirectories. Those in /media are automagically shown in the "places" display while those in /mnt are not; that's the difference between the two containers.

To mount devices automatically at boot time, the system has a file, /etc/fstab (File System TABle) that it uses to connect /dev "files" to other filesystems, possibly including /mnt or /media. The administrative user can also use the "mount" command to make such connections from the command line at any time, and some file managers such as Nautilus also have such a capability.

Now with all that background I'll try to answer your question. If you format the "/" filesystem, it will format all its offspring t**hat are on the same /dev device and are not separately identified to the formatting program.** Thus if you did not define a separate /home filesystem, your home directory would be wiped clean. However since you did define /home as a separate filesystem, it won't be included in the group to be wiped. You could also add definitions for any of the other top-level filesystems (those shown if you type "ls /" at the command line), to prevent them from being affected.

If you wanted to keep your own home directory and its subdirectories intact, but wipe out all the other subdirectories in /home, you could do so by changing the "/home" definition in the formatting program to "/home/petrasflorin" and that would do the trick. You can protect any filesystem the same way; it does not have to be at the top level of the hierarchy. 

Now for why your partitions are smaller than you requested. There are two possible reasons for this. One is that drive makers, and some programs, define kilobytes, megabytes, and gigabytes in strict decimal format as 1,000, 1,000,000, and 1,000,000,000 bytes respectively. Most programs, though, follow binary conventions: a kilobyte is 1,024 bytes, a megabyte 1,024 kilobytes, and a gigabyte 1,024 megabytes. By the time you get to a gigabyte, the difference between the two definitions is pretty significant! If one of your programs followed one of these conventions, and the other followed the other, you would see a significant "loss" of space.

But wait, there's more! Linux reserves about 5% of the space in each partition for use by the system itself. If you're a long-time user of Windows, you have probably run into the problem that happens when the system tries to use the very last sector on a drive. Apparently there's what programmers call a "fencepost" error in the disk-writing code way down at the lowest levels, so that the system never discovers that it's out of space and keeps trying to write, forever (or until you pull the plug). By reserving some of the disk for system use, Linux insures itself against such problems. It's possible to change the amount of reserved space, or even to do away with it altogether, but doing so isn't usually a good idea. Pulling the plug on a Linux system is a good way to corrupt your data and make it impossible to recover!

I hope this helps a bit. Getting used to the single hierarchy is a major change from the Windows way, but most of us find it easier to work with once the strangeness has worn off...

---

### Post by oldfred on 2010-10-10
I use a data partition, actually two. One older one that is NTFS for sharing with windows, but when I stopped using windows very much I created a /Data partition and mount all the folders into /home inplace of the defaults. Then /home only has system config files & folders fo less than 1GB so it is easy to backup.

I use the data partition as I install each new version of Ubuntu into another new partition and the newest rc,beta & final I may install several times just to test install. I want to mount my data into each install easily.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I did it manually the first time but then saved my history to a bash file and just run that with every new install.

---

### Post by petrasflorin on 2010-10-11
OK. I mainly got the idea. Partitions are show under "/" even if they are separate. For example, if I do mount|column -t I get:

/dev/sda7         on  /data                     type  ext4                   (rw,commit=0)

  OK ? Ok. Now this appears as a folder named "data" that is 365 GB large under the "Filesystems" directory in Nautilus. I've started to fill it up with music, movies and whatnot. 
  Basically, since it's mounted by itself, and it is indeed a separate partition, and based on what you explained about the offsprings of the "/", it shouldn't be formatted if I say... Reinstall Ubuntu and at the partition screen (Where I have / , /home , swap and /data) I choose not to format the /data, but all the others. Did I get it right ?

[http://img375.imageshack.us/img375/663/screenshotow.png](http://img375.imageshack.us/img375/663/screenshotow.png)

and 

[http://img801.imageshack.us/img801/855/screenshot1nj.png](http://img801.imageshack.us/img801/855/screenshot1nj.png)

and

[http://img684.imageshack.us/img684/8025/screenshot2qy.png](http://img684.imageshack.us/img684/8025/screenshot2qy.png)

---

### Post by nothingspecial on 2010-10-11
If I understand you correctly, yes.

---

### Post by JKyleOKC on 2010-10-11
Note that if you reformat /home, you will lose all of your personalized configuration information, and even your user account. If that's what you want, fine, but many of us choose to keep our home directories intact from one install to the next. 

I've done it both ways, and now retain the home directory (mostly because that's where my virtual machines are stored, in a hidden directory, and I don't want to lose all of them; I could move them to a separate saved filesystem but that would be a lot more work for no real advantage). Since you're pretty much starting from scratch, your approach should be fine.

---

### Post by petrasflorin on 2010-10-11
I prefer formating /home too because I install a lot of crappy unuseful **** that not only it is like I said crappy but it is (will) be the reason for my reinstalling of Ubuntu. Good to know the other /data partition is safe.

---

### Post by florinbelea on 2011-03-25
> **swagatmishra said:**
> everytime you install a new software using apt-get or synaptic package manager,
apt stores the downloaded packages at /var/cache/apt/archives.
you can delete those archives to free up space


10x man! I was looking for a way to save the files i have installed trough the terminal i case i want to reinstall the OS i needed the firefox update just in case... anyway 10x :p

---

