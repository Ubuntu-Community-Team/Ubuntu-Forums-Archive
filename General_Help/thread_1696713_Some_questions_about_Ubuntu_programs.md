---
title: "Some questions about Ubuntu programs"
date: 2011-02-27
forum: General Help
---

### Post by bazerka on 2011-02-27
Ok so I have been using Ubuntu for a few months, but considering how I am a total noob at doing alot of things on it i wanna get some background info about a few things before I start screwing with it.

1) On deviantart i see alot of people will totally customized desktops using something called GTK2, questions: how to get and how to use? (a nice tutorial page might help lol i cant seem to find it on google)

2) I have a computer running vista and I have Ubuntu installed onto it using Wubi. I am keeping the Windows because I need it to run the latest version of iTunes (unless wine can run it but I havent tried yet because my media folder is larger than the 30 gigs i have for ubuntu). I also want to keep my windows folders and Ubuntu folders completely seperate, so my question: is there a way to increase the partition size of Wubi to past 30 gigs? I have tried to use [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), but when i used it it successfully repartitioned but than i rebooted and it said that root.disk was missing and my entire Ubuntu was gone (lame i know). I also did all the recent updates from the update manager, but that shouldnt cause that problem should it?
     
       2) a) lol if possible i would like to entirely create a new partition on my computer and install Ubuntu from there (simplifies alot of things), but i cant seem to shrink my existing hard drive... the max i can shrink is it 1.4 gigs. Does anyone know how to increase that space? (I have a 300 gig hard drive with 230 gigs free i wanna create a new partition with 210 gigs for ubuntu leaving windows with only 20 gigs of free space). I have looked at using Gparted to redo the partitions, but it destroys windows and I dont have a Vista reboot CD and cant get one cause i live in china o.o.

Anywho thanks for the help!
-Baz

---

### Post by Frogs Hair on 2011-02-27
The link is for getting started with eye candy , sorry (not) I missed Vista 
but set my partition for Ubuntu from Win 7 disk management.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by bazerka on 2011-02-27
Ok I have a plan, but check to see if hypothetically it will work. I am getting a windows 7 installation disk from my friend so what i plan to do is to use gparted on my computer and resize the partitions. Than i will install windows 7 on top of vista to recover it and hopefully install windows 7 within the new partitioned hard drive. 
 
Or
 
I will install windows 7 ontop of vista (which from what i can tell will totally format and delete windows vista) and from there i can resize the partitions...
 
Does that sound like it will work? 
thanks
-Baz

---

### Post by jeremyjjbrown on 2011-02-27
> **bazerka said:**
> I have looked at using Gparted to redo the partitions, but it destroys windows and I dont have a Vista reboot CD
-Baz

Gparted does not destroy windows if you tell it not to. You have to boot from the livecd start the installer and Manually Specify Partitons. Of course there is risk involved so back up your files! Leave windows a nice area of space. An Ubuntu install shouldn't need more than 20-30 gigs.  

check out this for more...

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

### Post by Frogs Hair on 2011-02-27
I always install Windows first , but there is no reason you can't use Gparted . I have not tried a triple boot , and I think that is what your planning . What do is use Windows disk management to shrink the free space and select that space during the Ubuntu installation.

---

### Post by bazerka on 2011-02-27
The thing is i want to dual boot with windows, but i want to have ubuntu as my main operating system. The only reason for me to keep windows is just in case i want to have windows programs or something. 

So basically i want to:

- Split my 300 gig internal hard drive into 2 parts with a partition / 1 partition = 90 gigs and the other = 210 gigs

- Install windows on the 90 gig partition and ubuntu on the 210 gig partition.

---

### Post by libssd on 2011-02-27
> **bazerka said:**
> The thing is i want to dual boot with windows, but i want to have ubuntu as my main operating system. The only reason for me to keep windows is just in case i want to have windows programs or something. 

So basically i want to:

- Split my 300 gig internal hard drive into 2 parts with a partition / 1 partition = 90 gigs and the other = 210 gigs

- Install windows on the 90 gig partition and ubuntu on the 210 gig partition.
210 gb is HUGE for any version of Linux. What are you going to put in all that space? This guide provides some of the clearest thinking I have seen on the topic:  [http://forums.linuxmint.com/viewtopic.php?f=90&t=11872](http://forums.linuxmint.com/viewtopic.php?f=90&t=11872)

It's a little dated (use EXT4 instead of EXT3), but the basic concepts remain valid.

---

### Post by bazerka on 2011-02-28
Lol i want to put my entire computer on it o.o, i basically want to abandon my windows and only use ubuntu. I just want to keep windows for a "just incase there is just in case oh i dunno STARCRAFT" and i wanna play it rofl

---

### Post by libssd on 2011-02-28
> **bazerka said:**
> Lol i want to put my entire computer on it o.o, i basically want to abandon my windows and only use ubuntu. I just want to keep windows for a "just incase there is just in case oh i dunno STARCRAFT" and i wanna play it rofl

Nevertheless, read the entire piece I linked to for ideas about HOW to lay out your system, especially:

[I]2) Smaller partitions are faster than larger partitions.
[/I]

If you separate your OS and data partitions, you will find it easier for software migrations, and trying out other distros. A little planning now will reduce work further down the road.

---

### Post by bazerka on 2011-03-01
Yea, my computer is working now: i got a 90 gig partition with windows 7 and a 210 with ubuntu, but im wondering if i put the operating system on a smaller partition (say 20 gigs?) and the storage of files on the remaining 190 gig partition will the os run faster? (its fast now, but just saying it lags a little more than my 30 gig wubi install did)

---

### Post by jeremyjjbrown on 2011-03-02
> **bazerka said:**
> Yea, my computer is working now: i got a 90 gig partition with windows 7 and a 210 with ubuntu, but im wondering if i put the operating system on a smaller partition (say 20 gigs?) and the storage of files on the remaining 190 gig partition will the os run faster? (its fast now, but just saying it lags a little more than my 30 gig wubi install did)

No It won't run faster. But a shared data partition is very useful. You can mount and NTFS in both systems to keep your shared files. And, if you need to rebuild an OS you don't need to rebuild your data too.

---

### Post by libssd on 2011-03-02
> **jeremyjjbrown said:**
> No It won't run faster. But a shared data partition is very useful. You can mount and NTFS in both systems to keep your shared files. And, if you need to rebuild an OS you don't need to rebuild your data too.
I agree about the advantages of putting Linux in its own partition, and storing data elsewhere, which is why I linked to the post from the Linux Mint forum. If you're just doing Ubuntu (which should take up about 4gb), an 8gb is sufficient, and 16 gb would be more than sufficient for OS-only. I'm running Ubuntu on a 32 gb SSD, and OS + all my data still leaves 21gb free.

---

### Post by bazerka on 2011-03-03
Ahh interesting, well i took your advice and repartitioned my hard drive, so i have a 30 gig partition that is running ubuntu and a 180 partition that is rooted at /home for my storage devices. That way i dont have to open a completely new file system the home folder in the ubuntu os installation is directly on the other HD :), just save and interact as normal :). Using ubuntu and LOVING IT!

---

