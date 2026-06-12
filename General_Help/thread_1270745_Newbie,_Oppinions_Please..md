---
title: "Newbie, Oppinions Please."
date: 2009-09-20
forum: General Help
---

### Post by czanella on 2009-09-20
My computer is: Toshiba Satellite A215-S4757. I like Windows Vista for gaming, and it has a lot of good programs i use. But, I am a college student and am taking CST classes and I have discovered that Windows sucks for programming.... So I want Windows, But i also **need** Linux. Before i go start screwing with this computer(its my good computer) i need to know some facts and appreciate any opinions given.
If you know stuff that would help and aren't in my questions please still give. :)
1. I have Security Software on my laptop and i need to know would it still work for Linux? 
    1a. kind of still question but would my programs still work on Linux; like M.office? Firefox? System Mechanic?
2. Partitioning, I still want to be able to access all of my Hard Drive through either of my OS's, (ie; if i save a notepad.c doc on my Windows Vista in My Documents, then i want to still be able to pull that notepad.c document up off my Linux side.)
3. This computer is my baby, I try to keep it in best condition, So Screwing up my hard drive is not wanted, i know i can install Linux along side Windows but will that mean that Linux will be screwing with Windows OS?
4. Oh and lastly I'm not sure which Linux to use, This will be my first Linux computer(i have a ps3 with YDL but don't go on much.)so i just want some advice on which one to get. I would like the version to come with all the good stuff (Firefox, maybe so stupid games like minesweeper, gcc, ssh) and i am a gamer, need Open Office and all that. I saw a friend with Ubuntu that looked like mac, that would be cool, so any tips on that would be appreciated as well. 
Thank you in advance. :)

---

### Post by odinb on 2009-09-20
Install Ubuntu as your main OS (host), make sure you format it with a separate /home partition. Id you go for 9.04, I recommend running 64 bit, if older version, go for 32 bit.

I would recommend something like:

10-15GB for your os (/root)
2GB for your swap (/swap)
The rest for your home directory (/home)

Then you install virtualbox from Sun, and run Win XP in that as a guest, or if you have a powerful machine (quadcore), you can go for Win 7 as a guest.

You will not be able to run any games under Windows, but everything else office-related works just fine!

This works just fine for me and my office needs (Outlook, MS-Office, visio, MS-Project etc.)

For sharing files between the OS, you just map your /home from Linux as a drive in your guest.

This way you can run both OS at the same time, and do not force you to constantly reboot as you would have to with a dual-boot machine. Dual-boot often ends up with you mostly using just one OS, and unfortunately due to corporations forcing us to use Outlook, MS-Office etc, it tends to ends up being Windows...

---

### Post by czanella on 2009-09-20
Wow quick reply. :) 
And my Satelite is a 32bit version of Vista, So if i went to 64bit version of Ubuntu would it still work? And you talk about Windows 7, I havent heard much talk about it but all i know is that its like a quicker vista(i am definetly not buying it though). To be honest you really confuse me in "Then you install virtualbox from Sun, and run Win XP in that as a guest, or if you have a powerful machine (quadcore), you can go for Win 7 as a guest." (your throwing around MS Os names like thay are freely downloadable, lol and i wish i had quadcore)

And finally You said "You will not be able to run any games under Windows" this is a concern of mine because as i said i am a gamer.... is their any way that i can get games enabled?

---

### Post by staf0048 on 2009-09-20
To answer your program compatibility question, yes your programs should work just as they do now if you install Vista as a vitural machine through virtualbox.  

I have a Toshiba laptop myself, so just a fair warning in case you expect you can use the recovery CD that came with your computer to install Windows as a guest OS in virtualbox, it doesn't work.  I've tried everything under the sun to get it to work because there were a few programs I paid good money for that I really wanted to work.  Alas, I gave up.

However, I still got some programs to work and bypassing Windows all together by using Wine.  Most of the games I played in my MS days work, but some don't.  MS Office '07 does, except Powerpoint . . . I think.

If you PC is 32 bit, you will need to use a 32 bit OS.  It will not recognize 64 bit software.

---

### Post by odinb on 2009-09-20
Well, if you need games, that basically means you have to run windows as your host/main OS....

In that case, a dual-boot might be better for you, or perhaps swapping the guest and host.

Virtualbox is available for Windows also, so then you can run windows as you host, and install Ubuntu as your guest. Again share your host drive with your guest OS.

..and about the freely downloadable MS OSes, they are freely downloadable from MSDN if your employer has a subscription (or using torrents if they do not, but this is naughty I heard).

---

### Post by odinb on 2009-09-20
> **staf0048 said:**
> 
If you PC is 32 bit, you will need to use a 32 bit OS.  It will not recognize 64 bit software.

For virtualbox, your host can be 32bit, and you can still install a 64bit guest as of virtualbox version 3.

---

### Post by staf0048 on 2009-09-20
> **odinb said:**
> For virtualbox, your host can be 32bit, and you can still install a 64bit guest as of virtualbox version 3.

VERY cool and useful.  I was not aware of that.

---

### Post by 3rdalbum on 2009-09-20
> **czanella said:**
> 
1. I have Security Software on my laptop and i need to know would it still work for Linux?

Whatever it is, you don't need it. There are no Linux viruses in the wild at the moment. Firefox has anti-phishing built-in. If you run server services you should install something to deal with rootkits, but this sort of software is free.

> 1a. kind of still question but would my programs still work on Linux; like M.office? Firefox? System Mechanic?

Some versions of Microsoft Office can be installed in Wine on Linux, but Ubuntu comes with Openoffice.org which has MS-Office compatibility. Firefox is preinstalled.

When asking about whether a particular piece of software will work, or if there's a Linux replacement, can you please mention what the software does? I don't know if System Mechanic is something that tweaks or cleans up Windows, or if it's some sort of hardware monitor.

> 2. Partitioning, I still want to be able to access all of my Hard Drive through either of my OS's, (ie; if i save a notepad.c doc on my Windows Vista in My Documents, then i want to still be able to pull that notepad.c document up off my Linux side.)

Yes. Don't remove your Windows partition, just resize it with the Ubuntu installer.

> 3. This computer is my baby, I try to keep it in best condition, So Screwing up my hard drive is not wanted, i know i can install Linux along side Windows but will that mean that Linux will be screwing with Windows OS?

No. Linux doesn't understand Windows, so it won't touch Windows. The installer will resize the Windows partition downwards if you wish, and use the empty space for your new Linux files. It will change the MBR to point to its own bootloader, too, but this will also add the ability to boot Windows from the Linux bootloader (which is called GRUB).

Before performing ANY partitioning, make a back-up of EVERYTHING that cannot be replaced.

> 4. Oh and lastly I'm not sure which Linux to use, This will be my first Linux computer(i have a ps3 with YDL but don't go on much.)so i just want some advice on which one to get.

Yeah, just get Ubuntu. Biased advice I know, but for your use there's not any specific advantages to any distribution, except that Ubuntu has the biggest community, and it's easy-to-use. It's NOT Windows though; Ubuntu does things the Linux way, which you'll have to learn. It's user-friendly but different.

> And my Satelite is a 32bit version of Vista, So if i went to 64bit version of Ubuntu would it still work?

If your CPU supports 64-bit, then yes 64-bit Ubuntu will be fine for you. If it's running Vista already, I'm guessing it has enough RAM to warrant 64-bit.

Virtualbox is a piece of software that can run other operating systems inside a window.

> And finally You said "You will not be able to run any games under Windows" this is a concern of mine because as i said i am a gamer.... is their any way that i can get games enabled?

Linux isn't Windows. It doesn't natively run Windows programs. Windows doesn't run Linux programs. Mac OS X doesn't run Windows or Linux programs, and Windows and Linux don't run OS X programs.

There is a compatibility layer called Wine that can be installed, and allows you to use some Windows software; but less than 50% of Windows software will work in it (that's a guess) because Windows is a very complicated, moving target for compatibility.

There are native Linux games that you might enjoy.

You're going to be running a dual-boot system, right? (dual-boot is where you get the choice on startup whether you want to run Windows or Ubuntu).  If you set up a dual-boot then you can still run Windows games on Windows, which a lot of people do.

---

### Post by czanella on 2009-09-20
Alright this is good, i like the running Vitualbox on windows idea. So, Just to clarify, Do i still need to make Ubuntu Duel boot? And if not does that mean i dont partition anything? (would this mess with Windows?

---

### Post by 3rdalbum on 2009-09-20
> **odinb said:**
> For virtualbox, your host can be 32bit, and you can still install a 64bit guest as of virtualbox version 3.

Assuming your CPU is 64-bit and supports virtualisation extensions. Not all mobile processors do. It might be a bit buggy too; I can't seem to get 64-bit guest Ubuntu working correctly in a 64-bit host on Virtualbox 3, and that requires virtualisation extensions.

---

### Post by odinb on 2009-09-20
Another cool thing introduced in virtualbox 3 is multicore support for your guest ([http://www.virtualbox.org/manual/UserManual.html#settings-processor](http://www.virtualbox.org/manual/UserManual.html#settings-processor)), and Direct3D 8/9 applications support ([http://www.virtualbox.org/manual/UserManual.html#guestadd-3d](http://www.virtualbox.org/manual/UserManual.html#guestadd-3d)).

The Direct3D 8/9 applications support is still in its early stages though, but it looks promising....

---

### Post by odinb on 2009-09-20
> **czanella said:**
> Alright this is good, i like the running Vitualbox on windows idea. So, Just to clarify, Do i still need to make Ubuntu Duel boot? And if not does that mean i dont partition anything? (would this mess with Windows?

If you run Virtualbox in Windows, no dualboot needed, no partitioning needed. The guest OS harddrive will be a file on your host OS filesystem.

---

### Post by staf0048 on 2009-09-20
> **czanella said:**
> Alright this is good, i like the running Vitualbox on windows idea. So, Just to clarify, Do i still need to make Ubuntu Duel boot? And if not does that mean i dont partition anything? (would this mess with Windows?

No you will not need to dual boot.  Just download virtualbox from here:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

get a copy of Ubuntu (or whatever linux distro you choose) and install it to a virtual machine off of the ISO image download.  Virtualbox makes the process pretty easy, but you can always check back here if you have troubles.

You should be off and running with Linux in no time.

---

### Post by odinb on 2009-09-20
I prefer using the repo, that way you will always get the latest version and updates:

--== VirtualBox Repository howto ==--
Add the repository to your system's list of APT sources:
*For Ubuntu 8.04 "Hardy Heron" users:
	deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

*For Ubuntu 8.10 "Intrepid Ibex" users:
	deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

*For Ubuntu 9.04 "Jaunty Jackalope" users:
	deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free

Now add the public key using the following command:
	wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -
or for key, use 6DFBCBAE

Install dkms and virualbox 3.0 using the following commands:
	sudo apt-get install dkms
	sudo apt-get install virtualbox-3.0

Users might want to install the dkms(Dynamic Kernel Module Support) package to ensure that the VirtualBox host kernel module (vboxdrv) is properly updated if the linux kernel version changes during the next apt-get upgrade.

---

### Post by czanella on 2009-09-20
Nice post, very informing. :


"When asking about whether a particular piece of software will work, or if there's a Linux replacement, can you please mention what the software does? I don't know if System Mechanic is something that tweaks or cleans up Windows, or if it's some sort of hardware monitor."

System Mechanic is something my mom installed, it has a bunch of tools that like defrag and backup registry and stuff, its been useful, id like to have a similar tool with linux because if i do dual boot then that means my mechanic will only be defragging half my drive....

"Yes. Don't remove your Windows partition, just resize it with the Ubuntu installer."
ive got plenty of room for ubuntu already, not sure if a resize would be necessary i would like to be able to use my files on both systems which is why im looking into the virtualbox, still trying to understand it.
  
"It will change the MBR to point to its own bootloader, too, but this will also add the ability to boot Windows from the Linux bootloader (which is called GRUB).

Before performing ANY partitioning, make a back-up of EVERYTHING that cannot be replaced."

2 comments on this one is your talking about a bootloader i kindaa get what your saying but i guess i need to clarify, When i install linux it will change boot from Windows to Linux, but i will have a choice to boot either at startup right? And 2 if i need to backup my files does this mean im risking screwing up my pc? i have everything backed up, but im not sure i want to risk a $1000 dollar thing on freeware i just heard of..... This is a solid written Os right?

---

### Post by staf0048 on 2009-09-20
> **odinb said:**
> I prefer using the repo, that way you will always get the latest version and updates:

--== VirtualBox Repository howto ==--
Add the repository to your system's list of APT sources:
*For Ubuntu 8.04 "Hardy Heron" users:
	deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

*For Ubuntu 8.10 "Intrepid Ibex" users:
	deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

*For Ubuntu 9.04 "Jaunty Jackalope" users:
	deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free

Now add the public key using the following command:
	wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -
or for key, use 6DFBCBAE

Install dkms and virualbox 3.0 using the following commands:
	sudo apt-get install dkms
	sudo apt-get install virtualbox-3.0

Users might want to install the dkms(Dynamic Kernel Module Support) package to ensure that the VirtualBox host kernel module (vboxdrv) is properly updated if the linux kernel version changes during the next apt-get upgrade.

While this is best for Ubuntu machines, it will not work for Windows hosts.  You will need to download it off the net.

---

### Post by czanella on 2009-09-20
Haha wow you guys are very knowledgable, and very fast. sorry if im posting questions and they are answered in posts right before. Im a slow typer and im trying to google stuff while posting. Thx staf0048 and odinb. May i Pm you guys if i have any more questions? (if their is Pming in this forum.... (looking lol.)

---

### Post by odinb on 2009-09-20
> **staf0048 said:**
> While this is best for Ubuntu machines, it will not work for Windows hosts.  You will need to download it off the net.

Duh! stupid me! You are absolutely right! It is getting late here, and I always use Ubuntu as my host.

The package manager in ubuntu is spoiling us Linux users, think of the poor windows guys, having to update OS, all drivers and apps one by one, wasting hours, where I just do a sudo aptitude update && sudo aptitude safe-upgrade and lean back for 5 min and it is all done (if my repos are all setup)!

For tools like system mechanics, no defrag is needed on Linux, and cleaning your machine is done by sudo apt-get autoremove && sudo apt-get autoclean.

Indeed we are spoiled compared to windows users....

Will go sleep now!

---

### Post by staf0048 on 2009-09-20
> **czanella said:**
> System Mechanic is something my mom installed, it has a bunch of tools that like defrag and backup registry and stuff, its been useful, id like to have a similar tool with linux because if i do dual boot then that means my mechanic will only be defragging half my drive....

2 comments on this one is your talking about a bootloader i kindaa get what your saying but i guess i need to clarify, When i install linux it will change boot from Windows to Linux, but i will have a choice to boot either at startup right? And 2 if i need to backup my files does this mean im risking screwing up my pc? i have everything backed up, but im not sure i want to risk a $1000 dollar thing on freeware i just heard of..... This is a solid written Os right?

You won't need to worry about defragging the HDD.  With the way Linux works, it's just not necessary.

Regarding the boot loader, if you install Linux on a guest OS you will not need to worry about this.  Basically, you load Windows as you usually do, then you open Virtual box, from there you choose which guest OS you want to run (you can have several) and it will load in a new window - just like any other old program.  Going this route is the safest as it will not touch your primary OS.

---

### Post by jocko on 2009-09-20
> **czanella said:**
> System Mechanic is something my mom installed, it has a bunch of tools that like defrag and backup registry and stuff, its been useful, id like to have a similar tool with linux because if i do dual boot then that means my mechanic will only be defragging half my drive....
Linux has no registry and linux filesystems generally do not need defragging, so there is no program like system mechanic for linux.

If you are a gamer, you need to keep windows installed on your real machine, as virtual machines do not use the real hardware of your machine. So don't listen to the guys that tell you to install windows as a virtual machine in a linux host. Even if virtualbox does have experimental direct x support and may run some of your games, they will never work as well as on a real machine.
You need to set up a dual boot, or set up linux in a virtual machine in windows.

In a virtual machine, ubuntu will not use the real hardware of the computer, so it will not perform as well as it does on the real machine. But if you have lots of memory and a good cpu it can come pretty close to a real machine (except on the graphics side, as the virtual graphics card is definitely not as good as a real graphics card).

You can set up a dual boot as a "real" install with ubuntu on it's own partition, which require you to shrink the windows partition to leave room for linux. Messing with partitions is always risky, but if you use a windows tool to shrink the windows partition and defrag it several times before you start, only a power failure or a windows crash will cause data loss.

Or you can set up ubuntu as a wubi install, which means ubuntu will reside in a large file in the windows filesystem but will still run on your real hardware. This probably will not run as well as when ubuntu is on a real partition, at least I guess that the disk performance will be a little bit slower than it could be, but maybe the difference is not large enough to notice... This option will also give you the option to uninstall ubuntu from within windows if you by some reason realize that you don't want to keep it.

---

