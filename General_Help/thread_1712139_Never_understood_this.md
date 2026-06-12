---
title: "Never understood this"
date: 2011-03-22
forum: General Help
---

### Post by nkae100 on 2011-03-22
Since my time using Linux (10 months) I have come to learn that 'Linux distributions' really means **** at the end of the day a distribution is partially an excuse for a programmer not being able to keep regression away in his next code update.

I am going to be building a new computer soon and I am still not understanding somethings about computers, which I need to know about to accomplish this.

First, I am going to create an EXT3 file system. Who created EXT and where can I find their program?

---

### Post by conneco on 2011-03-22
[http://www.novell.com/documentation/suse91/suselinux-adminguide/html/apas02.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/apas02.html)

this tells you who designed ext3(Stephen Tweedie if you dont want to look), as for there program im not to sure what your asking for, there is no ext3 binaries as such its a file system,

---

### Post by nkae100 on 2011-03-22
Thanks for that dude! How would I create this file system though?

---

### Post by conneco on 2011-03-22
If your new computer is going to be running Ubuntu then its done on the install, you put the Ubuntu install disk in and as your running through it will ask how you want to format partition the disk, You can ever accept the install defaults and it will create a Ext3 file system on your hard disk or you can choose to manually create the partitions and choose from many other different file systems.

If you blindly click next through the ubuntu install, as I do a lot... then it will do all this for you without you having to give any input bar your name etc....

---

### Post by deathadder on 2011-03-22
You might want to have a look at a comparision of the different "main" file systems you can use in Linux, ext3/ext4/resiserfs although there are many of great filesystems to choose from (a geeky statement if ever there has been one). 

As conneco said there are no ext3 binaries as such, there's a number of different apps to actually format your partitions with the correct file system. So you may want to have a look at mkfs.ext3, mkfs.ext4 and mkfs.reiserfs. You can normally set the journal and block sizes etc. Although unless you understand what you're doing it's probably just as good to leave those options alone and use the defaults from the installer.

---

### Post by matt_symes on 2011-03-22
Hi

I you want to format a drive to extX have a look at the command

```
mke2fs
```

or use disk utility.

Kind regards

---

### Post by nkae100 on 2011-03-22
Donno why you guys keep on talking about Ubuntu. I clearly stated I want to compile the Linux kernel from source and I need to create a file system to compile it on.

I'm not using any distro. I am going to build everything myself. Distributions **** me off and I'm sick of them.

---

### Post by conneco on 2011-03-22
Your in the wrong forum then bud try:-

[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

---

### Post by r-senior on 2011-03-22
You probably need something like this:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by ppk on 2011-03-22
Almost every distro will have it's own partitioner tool for you to use on installation, allowing you to create the filesystems of your choice for different partitions. One thing you should consider is creating different partitions for /home and /, which will allow you to keep your personal files if you re-install your OS.

Some useful documentation :
[https://wiki.archlinux.org/index.php/Partitioning](https://wiki.archlinux.org/index.php/Partitioning)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

EDIT: didn't realize you were compiling from source. I'm afraid I can't help you then.

---

### Post by matt_symes on 2011-03-22
Hi

The ironic thing is you will need a distribution to build your distribution.

As has been stated Linux from scratch or Gentoo is the way i would go if you want to build everything.

Kind regards

---

### Post by deathadder on 2011-03-22
Afraid you didn't say anything about compiling from source... :)

It's a lot of work to get a system setup from stratch just compiling. LFS is what you want though. But be prepared for quite a few headaches. 

What is it you don't like about distro's then? I would hazard a guess you don't like the package managers and not distro's (since in that's all that is basically different).

---

### Post by WorMzy on 2011-03-22
If you just want to live on the bleeding edge, give Arch or Gentoo a whirl.

---

### Post by nkae100 on 2011-03-22
> **matt_symes said:**
> Hi

The ironic thing is you will need a distribution to build your distribution.

Kind regards

... and this is exactly the part I don't get. If this is true, then how did the first distro come about?


Friends, the reason I want to create my everything from source using official releases is because I am sick of distributors modifying official stable source.

I don't plan on being on the edge. I only ever use stable software. I just REALLY hate the Linux world being so branded "which Linux do you have, do you have this Linux, do you have that Linux". Linux should be Linux.

I know I am going to have many head aches ahead of me. I have found 90% of Linux developers are arrogant in a sense that they assume user knows everything.

You will all laugh at me, but later on this year when I don't have so many problems I am going to start my own distro of Linux. It will basically be a combination of the latest stable software compiled and ready to use. It will just be awesome and convenient.

---

### Post by deathadder on 2011-03-22
If you want just vanilla soruce (unmodified source code) then instead of compiling it yourself I would suggest looking at Slackware/Gentoo and Arch.

You may really like Gentoo, basically it just provides a way to easily (if not quickly) build vanilla source through a system that's derived from FreeBSD.

But back to your main question, because you're going to be compiling software you need somewhere to compile it from. A environment which has GCC (the Gnu C Compiler) and various other tools. What Gentoo use to do (it's been a few years since I've used it...) is create a live cd with the basic packages on it. You would boot into a bash prompt and then create / format / mount partitions and chroot into them. This effectively uses the bash prompt from the live CD in the host environment while you're setting up the software you need. 

The first Linux install would have been made off the back off minix (the Unix like OS Linus based Linux on originally). So it was the C compiler and libs from minix which were used to create the first Linux install. Once that was up and running (with the various compilers and libs available) Linux could be used to compile different versions of itself. Now you'll ask the same question myself and hundreds of others have asked, "How was the first minix compiled?". It's a long history of programming and environments, which stems from punch cards, but basically somewhere along the line some assembly was written that produced a usable environment. That environment was used to create the C programming language, which was used to create compilers and finally Unix. Once there was Unix, the derritives were able to be compiled and so on.

You may find some useful information from places like wikipedia on the history of OS development:

[http://en.wikipedia.org/wiki/History_of_operating_systems](http://en.wikipedia.org/wiki/History_of_operating_systems)
[http://en.wikipedia.org/wiki/History_of_linux](http://en.wikipedia.org/wiki/History_of_linux)

---

