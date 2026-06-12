---
title: "Dual Booting"
date: 2010-12-03
forum: General Help
---

### Post by DeathByLinux on 2010-12-03
Hey guys, 
              I am thinking about working on my brother and sister's laptops and needed some guidance. Both my sister and brother want me to install Ubuntu and Windows 7. I just want to know whether it's smarter to install Ubuntu first or Windows first. My sister's laptop will come with Windows 7 installed, so I HAVE to install Ubuntu after, but my brother's case is such that I can do either windows 7 first or Ubuntu first. Which do you guys recommend?
In the end, I want both computers to have Windows 7 and Ubuntu running so that they can switch between the two OS's whenever the needs arise. 
-DeathByLinux

---

### Post by sandyd on 2010-12-03
> **DeathByLinux said:**
> Hey guys, 
              I am thinking about working on my brother and sister's laptops and needed some guidance. Both my sister and brother want me to install Ubuntu and Windows 7. I just want to know whether it's smarter to install Ubuntu first or Windows first. My sister's laptop will come with Windows 7 installed, so I HAVE to install Ubuntu after, but my brother's case is such that I can do either windows 7 first or Ubuntu first. Which do you guys recommend?
In the end, I want both computers to have Windows 7 and Ubuntu running so that they can switch between the two OS's whenever the needs arise. 
-DeathByLinux

install windows 7 first.
Dont resize partitions using ubuntu, or you might screw up windows 7.

---

### Post by DeathByLinux on 2010-12-03
> **sandyd said:**
> install windows 7 first.
Dont resize partitions using ubuntu, or you might screw up windows 7.
That option may not work with my sisters' computer, because it will come installed with Windows 7 and I am guessing the person who installed it has consumed the entire drive... which means I probably have to reinstall windows 7 and then make the necessary partitions, and then install Ubuntu? Does that make sense?

---

### Post by Asmodai on 2010-12-03
Not really. Just have Ubuntu resize the Windows 7 partition, but before that, make a full HD backup using dd. In case the resizing fails, you can return to the previous state and try again.

---

### Post by oldfred on 2010-12-04
Vista & win7 have partition tools in their MMC. Generally it is best to use Windows tools on windows and Linux tools on Linux. But sometimes you need Linux to repair windows, but never vice-versa.

Windows has to be installed in a primary NTFS partition with a boot flag. It also installs in two primary partitions unless you set it up with one NTFS partition first. The reason for the hidden boot/recover partition is so you can encrypt the main install, but the boot partition cannot be encrypted.

The slight advance of installing windows first is that it always overwrites the MBR with its boot loader. But it is not all that difficult to reinstall grub2 to the MBR after a windows install.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by lisati on 2010-12-04
The conventional wisdom is to install Windows first, then Ubuntu, because Ubuntu usually plays nicer with existing Windows installs that you want to keep than Windows does with Ubuntu installations.

I've seen sporadic reports of Ubuntu's partition manager hurting Vista and Windows 7 installations, hence the advice to use the Windows partition manager on Windows partitions. It happened to me once, and I didn't "join the dots" too quickly because the repair was fairly straightforward.

---

### Post by DeathByLinux on 2010-12-05
Ok, you guys are gonna hate me, but I need to tell you this, to convey what a newbie I really am. I JUST found out that my brother's computer has an extra ****ing harddrive. He has 2 111gig hard drives on his computer. I am just going to install ubuntu on his other harddrive and keep his windows as is, and just set up a dual boot.
I haven't gotten my sister's computer yet, but that will be the challenge, now. 
I will do it tonight, and then get back to you guys.

---

### Post by DeathByLinux on 2010-12-06
Okay, guys, here's the situation.
I popped by bootable flash drive with ubuntu and fired up the installer and I have hit a bit of a snag. I say a bit because I think I know what to do, but would still like some guidance.
I have arrived at the "Allocate drive space" portion of the installer and I chose to specify how I want to dish out space for the system. I could have chosen the "Install along other operating systems", which gives me the answer I think I need to choose, but here's what it shows at the advanced option.
So, as I understand it, the laptop came with 3 partitions on it. 
/dev/sda
/dev/sda1-fat32-size10485MB-used8746MB
/dev/sda1-ntfs-size119792MB-used87413MB
/dev/sda3-ntfs-size119778MB-used3221MB

I guess my biggest problem with the procedures is that I don't understand partitioning as well as you guys do. My guess is that sda1 is some sort file system (don't know what it does), sda2 is where vista and all the stuff my brother has is on, and sda3 is what I thought was the extra drive, but it turns out that it is a huge partition but don't really know why it was created. Shed light/correct me if I am wrong, anywhere.
Anyway, when I select the "Install along other operating systems" it automatically selects sda3 (which is what I wanted to do) and gives me the option of either using the entire partition, which is what I want to do, or using the entire disk, which I think will just erase the partitions and install an ubuntu partition.
I think I know what to do, but need some help anyway to make sure I don't erase the vista partitions. Should I go ahead with the suggested sda3 option in the "Install along other operating systems"?

---

### Post by wilee-nilee on 2010-12-06
You need to shrink one of the NTFS partitions, with the windows disk manager, and install to the unnalocted space left.

You might post this so we know more about the setup,
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

If it is choosing sda3 that makes no sense it is a ntfs, Linux doesn't install in a NTFS unless your doing a wubi install.

Look at oldfreds post the information is there and post the script.

---

### Post by sandyd on 2010-12-06
Sorry about my absence, a major RAID failure + some huge internet issues put me off for a while.

Reading here -> [https://help.ubuntu.com/community/RecoveringWindows#Resizing a Windows Partition in Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing a Windows Partition in Windows)

should show you how to resize the partitions properly ;)

---

### Post by Sofatiger511 on 2010-12-06
I used Windows 7 disk management tool to shrink the drive into second partition unallocated. That is safe and will not screw up Windows 7 already installed. Then install Ubuntu 10.10 via customs select partition one for root and one for swap. Windows 7 coexists happily with Ubuntu in such a set up.

Unfortunately, I am facing a problem to repeat the same set up with my newer Acer laptop. I would appreciate if someone can help me or guide me to find help as I  am having problem of setting up Windows 7 dual boot with Ubuntu 10.10 in  a 32bit machine. My laptop is Acer Aspire 9410 OEM Vista Home Premium.  Installing Windows 7 was not a problem. For some strange reason, when I  install Ubuntu, the DVD drive seems to have problem of reading and  converting program files  into readable screen. At the end of DVD  installation, the mouse cursor is not pointing arrow shape but a fuzzy  square. I can see Ubuntu window dialog frame but not the contents. I am puzzled. Anyone has any suggestion?

I tested and re-tested the read and write of the DVD and there is nothing wrong. Anothr strange behavior of my Acer Aspire 9410, it would not allow g-parted partition utility to boot even BIOS clearly set-up DVD first priority boot . It did partial boot by reading first 2 lines Isolinux---------- and then went dead.

---

### Post by DeathByLinux on 2010-12-06
Okay, so I did something that makes things easier (I think?). 
I simply deleted the sda3 partition, which gave me the space that I was being denied. I have all the space I need to work with. (Vista is unharmed, don't worry guys.)
Now, I need some guidance on the installation of Ubuntu.
So, at the Allocate drive space section, I need to learn how much space to put in what areas. 
For example, I know that "/" is the ubuntu systems folder. That is where all the applications for linux are located, when I install them. When I installed my current ubuntu, my friend told me to allocate at least 30gigs to that. The /home is where all my data is stored (movies, songs, etc). Now, there was one last thing that my friend partitioned for. Something called "swap" or something? So, this is my last step before I install Ubuntu. 
So, in Gparted here is what the MY computer looks like:

/dev/sda1, linux-swap, size 972.65MB, used ---, unused ---, boot
/dev/sda2
             /dev/sda5 ext4, /, 28.61 GB, used 4.00GB, unused24.61GB
             /dev/sda6 ext4, /home, 156.75GB, used 107.09GB, unused 49.66GB

So my question is a stupid one: what is the mount point name for "swap" and is that the only other thing I need to partition for before hitting the install button? (Note: when I say "mount point name," I mean, "what does it look like in the selection screen?" There are a bunch of "/" options, like "/home", "/boot" etc.)

---

### Post by oldfred on 2010-12-06
this is my standard recommendation. 30GB is generous if you have a separate /home but ok.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.

---

### Post by shoot2kill on 2010-12-06
A quick question, initially you say you want to install win7 & ubuntu, but in your last post you say 'Vista is unharmed, don't worry guys'

is this just a mistake and you mean win7, or are you planning on upgrading your vista to win7? if the latter, I would do that before installing ubuntu as win7 will probably override your boot record.

---

### Post by DeathByLinux on 2010-12-06
To Shoot2Kill: Yeah, I kind of changed my mind in mid way and decided that I am going to keep his Vista install and will not bother with the pain of installing windows 7 on his computer, since the only reason he wants it is for flash and in case he ever has to use a windows program that linux will not support (even thought I told him about WINE). I should have mentioned that, I am sorry. However, I am pretty sure that my sister's computer will come installed with windows 7, so I will need to work with it when I get my hands on that computer.

Status report:
Success!
Something really strange happened. Strange in a good way. So I installed linux with 3 partitions (3GB for Swap, 25GB for /, and rest for /home), and then rebooted and for some weird reason there is a dualboot style set up in place for me, that allows me to choose between vista and ubuntu, without having to do some crazy terminal guerrilla computing. The selection screen is called "GNU GRUB Version 1.98 blah blah 5Ubuntu3" or something. I am happy with the set-up but I don't know what happened. Explanation?
In any case, my brother's computer is done, and now I will move on to my sister's, whenever I get my hands on it.

---

### Post by oldfred on 2010-12-06
That is how it is supposed to work :), its just here in the forum we see all those who seem to have problems. Hopefully your sister's works as well.

But many new computers with win7 use all four partitions and you have to decide what to delete. You should make the backup DVD's that let you restore system to as purchased (but never really paln on using as it puts system back to as purchased with all your updates & data erased). If you can create a repair CD do that. Or download a win7 repair CD.
Often the vendor partitions with just a few utilities can be easily copied and then restored into a logical partition if need be. But then you have a primary partition you can convert to the extended partition and within the extended create all the partitions you need.

---

### Post by DeathByLinux on 2010-12-07
Well, I am glad that I got this far and the only problem I foresee with my sister's is the resizing partitions or something. I am gonna close this thread and I'll make another one, should I run into any problems with the next project.
In any case, I can't tell you guys how much of a help you all have been. I felt nervous about posting some of the dumb problems I ran into, but you guys were very patient.
Thanks Oldfred, Shoot2Kill, Sandyd, Asmodai, lisati, and wilee-nilee. Sofatiger511, hope your problem gets addressed and thank for your help, as well.
-DeathByLinux

---

