---
title: "Boot installed system to RAM"
date: 2010-12-09
forum: General Help
---

### Post by v5ar on 2010-12-09
I'm not a newbie, but I just have no time to research for myself,
I've seen many examples of booting livecd
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)
[http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230)

even the What 10.10 Needs: Boot to RAM
[http://ubuntuforums.org/showthread.php?t=1446301](http://ubuntuforums.org/showthread.php?t=1446301)

but there is no real solution how to boot installed sytem to ram

my hard drive in laptop broke, so i've installed ubuntu to usb,
but it's slow, and since my laptop has 4gb of memory, there would be no problem in loading some parts to memory, or even whole (lubuntu) system

preload and prelink are nothing, i don't know what should i mount to memory for faster acces so I beg for help! ramdisk, anything else?

i need it, i have to wait one month for new hard drive, and even with that i don't see whay shouldn't i load everything or most of the system to ram if i have enough ram memory

usb live is not an option, since you actually can't install programs and upgrade system and other operating systems are just not so complete, only option would be puppy, but latest has problem with autoconfiguration of my graphics card, and there is no option i've seen to do it manually, and older ones, are OLDER and incomplete in many areas


cheers!

---

### Post by mastablasta on 2010-12-09
you could make persistent USB live.
 
what about slitaz?

---

### Post by v5ar on 2010-12-09
persistent usb live only saves document and settings, etc, it's not real system and doesn't work that well, i've got many notifications about craches

slitaz i've seen, don't know why haven't tried it, but I will!

i'm still interested in using tmpfs or something to mount system there and then recopy everything at shutdown to usb (i don't restart it often, or at all)

EDIT: yes, i have no ability to boot from cd also, so i prefer and have to use live usb but it's not that easy to set up every distribution to boot live from usb (most of them are, but those have no boot to ram option when installed), and it's even harder when u have os on usb because everything is slow, i actually takes alot of time to setup and test all those solutions and distributions in my situation

---

### Post by C.S.Cameron on 2010-12-09
There is a thread around about making Ubuntu insanely fast by booting in RAM, There is also a script to accomplish this.
Unfortunately I don't have the time to post the link.

---

### Post by v5ar on 2010-12-09
i think you think about this 
[http://ubuntuforums.org/showthread.php?t=1603423](http://ubuntuforums.org/showthread.php?t=1603423)
?

but it's actually about making livecd toram feature

probably should open it and see what it does, that could help, but still if someone already have done it or knows how to, why not hear him/her

EDIT: nothing useful there, just adds and option to boot to ram in menu instead of providing toram parameter

---

### Post by arubislander on 2010-12-09
You mentioned wanting to install software and also upgrade the system in addition to running it from RAM. I don't think there are ready made solutions that do exactly what you're looking for.

---

### Post by v5ar on 2010-12-09
why not? your system is copied to ram, you use it normaly, install, upgrade, and in the end everything is written back to usb when you wan't to shutdown?

still, that doesn't have to be THE solution, it could be as simple as loading some directories to memory that are most accesed (/usr? and /tmp of course) to minimze usb overhead, and at the end, write back everything from memory to /usr directory on usb

---

### Post by JohnnyC35 on 2010-12-09
what about using unionfs or software raid1 and setting a 2Gb partition with 2Gb of space, or some such?

---

### Post by terminator14 on 2010-12-09
What you may be looking for is this: [URL="http://ubuntuforums.org/showthread.php?t=1594694"]http://ubuntuforums.org/showthread.php?t=1594694
[/URL]
It's basically a script I wrote that will take your existing OS and make a squashfs image out of it. At boot, that squashfs image will be copied to RAM and run from there. You can either tell the script to make a usb drive device into your /home, or just have the /home on RAM too and save any files you need to the usb drive.

The way you would use the script in your case would be this: install a regular OS to a usb drive (yes, this will be slow and take a while). Then, boot into that OS and run the script. Once it's done running, reboot and you will have an option in your grub menu to boot from RAM where a squashfs image the script created will be copied to RAM and the OS will run from there.

The script also comes with 2 other scripts: rupdate (which lets you run updates on the squashfs image) and rchroot (which helps you change config files on the squashfs image).

It's pretty easy to use once you get the hang of it.

---

### Post by C.S.Cameron on 2010-12-09
> **terminator14 said:**
> What you may be looking for is this: [URL="http://ubuntuforums.org/showthread.php?t=1594694"]http://ubuntuforums.org/showthread.php?t=1594694
[/URL]
It's basically a script I wrote that will take your existing OS and make a squashfs image out of it. At boot, that squashfs image will be copied to RAM and run from there. You can either tell the script to make a usb drive device into your /home, or just have the /home on RAM too and save any files you need to the usb drive.

The way you would use the script in your case would be this: install a regular OS to a usb drive (yes, this will be slow and take a while). Then, boot into that OS and run the script. Once it's done running, reboot and you will have an option in your grub menu to boot from RAM where a squashfs image the script created will be copied to RAM and the OS will run from there.

The script also comes with 2 other scripts: rupdate (which lets you run updates on the squashfs image) and rchroot (which helps you change config files on the squashfs image).

It's pretty easy to use once you get the hang of it.

Yeah, this is the one I was talking about.
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)
I was wondering how big a flash drive is required to do this?

---

### Post by arubislander on 2010-12-10
Only thing is that package and kernel upgrades aren't easily persisted, even though that is also a requirement for the OP...
But the concept is interesting and I'll be sure to give it a spin at the earliest convenience.

---

### Post by terminator14 on 2010-12-10
> **C.S.Cameron said:**
> Yeah, this is the one I was talking about.
[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)
I was wondering how big a flash drive is required to do this?

If you are going to install the OS to a flash drive, and run the script from there, it needs to be large enough to store the installed Ubuntu OS, a copy of the OS (excluding the /home folder) which will be your /var/squashfs, and a squashfs image in your /live.

I'm not sure of the exact size a freshly installed Ubuntu takes, but you'd probably need at least an 8GB drive. Anything less and you have a good chance of running out of space at some point while the script is running. This is more of an educated guess though and I could be totally off. If you need more space, you can also split up the 3 parts - Installed OS, /var/squashfs, and /live/filesystem.squashfs, to more than one flash drive.

---

### Post by C.S.Cameron on 2010-12-10
Thanks Terminator:
I downloaded your script the first day it was out, but only had a free 4GB flash, I figured not big enough. Will try it as soon as I have an 8GB free.
Hopefully V5ar will keep us posted on his progress.

---

### Post by v5ar on 2010-12-12
> **C.S.Cameron said:**
> Thanks Terminator:
I downloaded your script the first day it was out, but only had a free 4GB flash, I figured not big enough. Will try it as soon as I have an 8GB free.
Hopefully V5ar will keep us posted on his progress.script works just fine, for what i need it, it does its best!

installed ubuntu has size of about 3.2GB, which you can trimm down, to about 2,5 or 2.0gb and still have usable system, but instead of going further...
lubuntu occupies ~1.7GB, which results in ~3.4GB requirement, since ubuntu installer on 4gb usb makes 3.5GB partition and from rest creates swap, it works just fine, still, ~100mb of space, in best case, is a small amount to have, especially when you are having big system update (new kernel, openoffice...) and won't be enough...
anyway, you can have fully working lubuntu distribution that boots to ram with this script

PS
dont run this script like sudo sh RAM_booster.sh, it wont work properly :)

---

### Post by terminator14 on 2010-12-12
This is somewhat off topic but

> **v5ar said:**
> PS
dont run this script like sudo sh RAM_booster.sh, it wont work properly :)

Never run your scripts like that. Every script should have a [hashpling]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29") as the first line (like #!/bin/bash or #!/usr/bin/env python), to tell linux what environment to run the script in and with "sudo sh RAM_booster.sh", you're basically telling it to ALWAYS ignore that line and force it to run  in /bin/sh. This will only work on scripts that are written in sh, but because scripts are written in many different environments (many of which are in bash), and pretty much all scripts have an automatic way of determining what they should run in (the hashpling), just tell them to run in the environment they were written for:

```
sudo chmod a+x script
sudo ./script
```

---

### Post by Nextgeneration on 2010-12-23
Terminator14 I went onto your thread on how to get your os to boot off ram and downloaded the file maby I didn't catch it but how do I run it?

---

### Post by terminator14 on 2010-12-25
> **Nextgeneration said:**
> Terminator14 I went onto your thread on how to get your os to boot off ram and downloaded the file maby I didn't catch it but how do I run it?

First, extract the tar.gz file either with GUI tools (the default is file roller, just double click the file to open it), or in terminal cd to the same directory as the file and type:

```
tar -xzf RAM_booster.sh.tar.gz
```

once it is extracted, give yourself execute permissions with:

```
chmod a+x RAM_booster.sh
```

and run it by simply typing:

```
./RAM_booster.sh
```

Answer a few questions, wait a while for it to finish, and reboot. That should do it.

---

