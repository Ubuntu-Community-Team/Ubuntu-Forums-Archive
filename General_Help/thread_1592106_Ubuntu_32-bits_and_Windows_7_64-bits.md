---
title: "Ubuntu 32-bits and Windows 7 64-bits"
date: 2010-10-10
forum: General Help
---

### Post by Tallin91 on 2010-10-10
Hey there,

I'm entirely new to the unbuntu Community and tried to google/search a bit for the solution to my problem.
It turns out that I'm not really good at this :(

Hopefully somebody here could help me ^^

The scenario:

Hp Elitebook 8530w with windows 7 (64-bit)

What I want:
To install Ubuntu along windows 7 in order to make my life easier (in the way of, seperating study 'n games)

What I did:
Ubuntu, 32-bit is the recommended version, thus I burned the image... booted it... and then I ran into a problem at the part were it says "allocating drive space"

There is no option that says: Install alongside other Operating System.
Tried to create a partition... but it says something like: No root file system is defined.

Besides. partitioning isn't exactly what I was planning on... since it warns me for erasing the current state of my drive.

Any Idea what I can do about this? I just want to use ubuntu for study-purposes. so I don't mind what bit-version it is or w/e.
bit
Greetings Chris

---

### Post by mjitkop on 2010-10-10
Hi Chris,
you have 2 options if you want to install Ubuntu alongside Windows:

1/ use Wubi to install Ubuntu. This way, Ubuntu will be installed as if it was a Windows application but it will still boot as a standalone Ubuntu installation. This also has other benefits: no physical changes are made on your hard drive and your current partitions will be unchanged, and if you want to remove Ubuntu you just uninstall it from Windows as if you were uninstalling a Windows application.

2/ if you want to install Ubuntu in its own partition, you need to choose the second option from your first screenshot to specify partitions manually. What you need to do is resize your Windows partition to make it smaller and make room on your hard drive for Ubuntu. Even though this process should work fine, it is strongly suggested to backup your precious data before making any changes to your partitions. Once you have downsized your Windows partition, you will need to use the free partition to install Ubuntu in it.

I can't really give you more specifics at this point without seeing what you have on your hard drive. Maybe somebody else can help a little more.

As for 32 bits versus 64 bits, I can't advise you on this because I do not have any machines in my house that are 64 bits.

---

### Post by Mark Phelps on 2010-10-10
> **mjitkop said:**
> What you need to do is resize your Windows partition to make it smaller and make room on your hard drive for Ubuntu. 

NO ... do NOT do this!  Allowing the Ubuntu installer to shrink the Win7 OS partition is asking for trouble.

Much better way to do this is to shrink the Win7 OS partition using the Win7 Disk Management utility.  Leave the new space as unallocated.

Then, when you run the Ubuntu installer from the CD, choose the "largest free space" option.  The installer will then format the free space for you.

If you don't see that option, there is the possibility that your PC already has the maximum number of 4 Primary partitions.  That will make installing Ubuntu a LOT harder.

---

### Post by mjitkop on 2010-10-10
> **Mark Phelps said:**
> NO ... do NOT do this!  Allowing the Ubuntu installer to shrink the Win7 OS partition is asking for trouble.

Much better way to do this is to shrink the Win7 OS partition using the Win7 Disk Management utility.  Leave the new space as unallocated.

Then, when you run the Ubuntu installer from the CD, choose the "largest free space" option.  The installer will then format the free space for you.

If you don't see that option, there is the possibility that your PC already has the maximum number of 4 Primary partitions.  That will make installing Ubuntu a LOT harder.

Hi Mark. Thanks for correcting me. My experience with Ubuntu installation alongside Windows is only with Windows XP so I have no knowledge of possible problems with Windows 7. I didn't even think that it would be different than with Windows XP but in a way I am not that surprised now that you have mentioned it.

I stand corrected.

Good luck to Chris. :)

---

### Post by Tallin91 on 2010-10-10
Hey Guys,

Thanks for the usefull and quick responses. I'll try wubi! :)

greetings Chris

---

### Post by Quackers on 2010-10-10
I think the general consesnsus is to stay away from Ubuntu 10.10 Wubi for the moment. It is known to have some bugs (which will shortly be fixed, I'm sure). Try 10.04 perhaps.

---

### Post by Tallin91 on 2010-10-11
I kept on getting the same error.

I found this thread that should've contained the solution to my problem but the link
of the second poster, reffering to wubi 511+ is dead =(
[http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)

Downloading 10.0.4.1 now. Hopefully it'll work :)

Greetings Chris

---

### Post by Tallin91 on 2010-10-11
Oh, btw:

For those who're curious to the weird effects Ubuntu had on my laptop:

After the first time booting ubuntu my screen resolution was set to 800x600 as well as in ubuntu as in windows.

I've got three mouses, the little stick-thing in the middle of my keyboard, a touchpad and a wireless usb-mouse.

both the stick-alike-mouse and the touchpad were disabled after booting Ubunti and my soundcard was turned off.

weird eh? :)

---

### Post by Tallin91 on 2010-10-11
Update:

downloaded Ubuntu 10.0.4.1.
Used Daemon Tools instead of burning to a CD this time.

Uninstalled the old ubuntu, installed the new one. Same Error:

No root file system defined. -> Ubuntu not usable
and again my windows OS was totally messed up again, it crashed at the startup.

Windows is working now luckily but Idk what to do about this, despite the uncomfortable experiences with Ubuntu till now I'm still focussed on getting it working... I just lack the knowledge to solve this mysterie so any help is welcome :)

greetings chris

---

### Post by mastablasta on 2010-10-11
you were advised to use partitions to propperly install Ubuntu. you can't use daemon tools for system instalation. partitioning should be painless.
remember to defragment the driver first one or two times, backup anything that is really really importnant, do the partitioning (make a free partition) and that's it. continue the install from there.
 
btw you can also just boot from the CD into live session (change the bios boot order) to first test how well the Ubuntu system works. 
 
Also you might need to enable (load) some drivers for that screen of yours after a successfull OS isntall.
 
Wubi has issues (also in 10.04). it's ment to try out the OS, much like using live cd. also sometimes the easy way is not the best way. still for some it works for others it messes up itself sooner or later.

---

