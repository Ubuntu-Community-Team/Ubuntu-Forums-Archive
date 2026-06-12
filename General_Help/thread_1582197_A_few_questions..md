---
title: "A few questions."
date: 2010-09-26
forum: General Help
---

### Post by xNihil on 2010-09-26
Hello, I'm new to using Ubuntu and so far I'm loving it, but I have a few questions.
First of all, I'd like to install Windows 7 on my laptop (which currently has the latest version of Ubuntu installed) some time in the future, as well as create a few partitions to store files on without either system being effected. But before that I made the mistake of installing Ubuntu with another Ubuntu installation creating two partitions (luckily my data was still stored on the /home/username folder). I moved my files to the newer installation then formatted the other partition (to ext4), but apparently 6GBs or so were still used by the formatted partition. I then moved my files back to that partition. Now, every time I startup my PC, I have to choose which system to boot in (even though I formatted the partition with the older Ubuntu installation). To be on the safe side and not cause any errors or damage to the PC, I haven't tried booting the PC with the older system.
Here's my current partition layout (according to the System->Adminstration->Disk Utility):
    1. 159GB ext4 (the one with my files on it)
    2. 79GB ext4 (the one with my system on it)
    3. 3.4GB swap
    4. 8.5GB swap
    5. 91GB "extended" (What is that? It clearly exceeds the 250GB disk space)
Now, here's how I want my 250GB harddisk to be partitioned:
    1. A 7.5GB partition for my Ubuntu installation
    2. A 20GB partition for my Windows installation
    3. A 40GB partition for my Windows games and applications
    4. A partition taking up the rest of the harddisk's space for other uses (and swap space, whatever that is)
How can I achieve that without losing any of the files that I have, knowing that I don't have an external harddisk?
Also, do you have any pointers on improving a computer's speed and performance with Ubuntu installed on it?

---

### Post by micha8l on 2010-09-26
That seems like a lot of partioning you're doing on one drive, I'm not sure of the implications it'll have on your system, but I guess it can't be good.

If I were you I'd try installing your windows instillation in [www.virtualbox.org]("http://ubuntuforums.org/www.virtualbox.org") I myself use this for WindowsXP, but I generally use it for testing websites and nothing intensive like gaming - works well for me.

You mentioned not having an exteral hard-drive... oh but you do Ubuntu One offers you up to 2GB of free space on their cloud system, you could make use of that.

---

### Post by lykeion on 2010-09-26
What I would do if I were you is:

1) backup your data to external media (CD, USB drive)
2) install windows 7 (erase all data and format whole drive)
3) shrink the windows partition to make room for ubuntu
4) install ubuntu

And I would agree with micha that there's too many partitions on one drive. 
I don't know about the performance (with modern games for instance) when running Windows in virtualbox though. 
Personally I haven't used Windows since XP, but it's always been a resource hog OS.

Some links where you could find info on terms like extended partition, swap, etc
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

Regarding "improving a computer's speed and performance": There's lots to be said about this (and it's a very vague question also).
I think installing the proprietary driver for your graphic card will be the most drastic improvement you'll notice as a common user. Others may disagree.

---

### Post by xNihil on 2010-09-26
Ah. Thank you. ^^
In that case I'll have three partitions then, since I'm only going to use Windows for gaming and Photoshop (to be honest, I dislike GIMP).
But then how does one "shrink" a partition? Is this the option in the Ubuntu installation where one chooses to install Ubuntu side by side with Windows? And also, how do I create the third partition, in this case?
Finally, I apologize for the vagueness of my question.
Also, I do know about the free 2GB of storage, but first of all my upload speed is abysmal, and second of all, the files I'm talking about amount to about 60GB. :P
Furthermore, how does one "clean" their Ubuntu? In Windows, temp files and registries need to be cleaned out (among other ways), are there such things in Ubuntu? I know that temp files in Ubuntu get deleted when one boots their computer, if memory serves.
All the help is appreciated. Excuse my lack of knowledge.

---

### Post by sendblink23 on 2010-09-26
> **xNihil said:**
> Ah. Thank you. ^^
In that case I'll have three partitions then, since I'm only going to use Windows for gaming and Photoshop (to be honest, I dislike GIMP).
But then how does one "shrink" a partition? Is this the option in the Ubuntu installation where one chooses to install Ubuntu side by side with Windows? And also, how do I create the third partition, in this case?
Finally, I apologize for the vagueness of my question.
Also, I do know about the free 2GB of storage, but first of all my upload speed is abysmal, and second of all, the files I'm talking about amount to about 60GB. :P
Furthermore, how does one "clean" their Ubuntu? In Windows, temp files and registries need to be cleaned out (among other ways), are there such things in Ubuntu? I know that temp files in Ubuntu get deleted when one boots their computer, if memory serves.
All the help is appreciated. Excuse my lack of knowledge.

Upon going to install Ubuntu.. that is where you can shrink the size of your Windows 7 install

---

### Post by JohnElway on 2010-09-26
> **sendblink23 said:**
> Upon going to install Ubuntu.. that is where you can shrink the size of your Windows 7 install

I've heard many people recommend using Windows' built-in tools for partition shrinking.

Check method one here: [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

---

### Post by Lateralis on 2010-09-26
**DO NOT** use Gparted to shrink your Win 7 partition.  Win 7 comes with partitioning tools.  Always use those to fiddle around with Windows partitions, *particularly* those relating to the Windws OS partition. 

I don't recall where the tools are located in Windows 7, but they are there.  If you search around the internet I'm sure you'll figure it out.  

Similarly on this front, try not to read/write unnecessarily to the Windows 7 OS partition.  If you can afford a shared partiton which is to contain all of your documents, music, videos and so forth, then do that.  

As for partitioning generally... A standard was set many moons ago that said a hard drive can have a maximum of 4 primary partitions.  This eventually provided to be a major limitation, so a workaround was found, called extended partitions.  You can think of these as being containers.  Each extended partition can hold a large number of partitions (I forget how many, but 255 rings a bell).  In this way you can divvy up a hard drive into an arbitrarily large number of partitions, provided you have no more than 4 primary partitions.  An extended partition counts as a primary.  

The numbering of partitions is straightforward, but does confuse newer people.  All primary partitions are labelled 1-4, but an extended partition must have a number greater than 4.  For instance, suppose you have 1 Win primary partition, 1 NTFS shared drive with data and things and then an extended partition containing Ubuntu and a Swap area.  The partitions are numbered like this:

sda1 - Win OS
sda2 - NTFS shared
sda3 - Extended
sda5 - Ubuntu root (first partition in an extended partition)
sda6 - swap.    (second partition in an extended partition)

As for "temp" files in Ubuntu (and Linux)... you don't need to worry about those.

---

### Post by xNihil on 2010-09-26
Ah. Thank you. I think I understand now.
I've decided to install Windows 7 and then wait for Ubuntu 10.10's official release to install it alongside it. 
I'm currently learning how to program and I look forward to improving Ubuntu in whatever meager way I can.

---

