---
title: "Stumbled onto ubuntu - can't boot windows"
date: 2011-03-27
forum: General Help
---

### Post by jwiddy on 2011-03-27
Here's my story.  I bought an HP pavilion laptop i3 64 bit (which I totally regret) for recording some music with cubase and running electric drumming midi software (bfd2)     I was having all kinds of compatibility issues with the preinstalled windows 7 so I wanted to try using XP instead.  Couldn't format the hard drive, and I stumbled onto a thread saying i could use ubuntu to blow away the windows 7.  I tried  ubuntu, and i now really like it so I'd like to try and dual boot with XP, and I used gparted to partition the HD.  I tried two different versions of XP disks.  One is XP professional 32 bit and the other is 64bit.  The 64bit starts windows but then gives me a blue screen error saying "a problem has been detected and windows has been shut down to prevent damage to your computer.  Then mentions a "stop" error 0x0000007b.  The 32bit version doesn't even get recognised.  Any suggestions on how to make this work?

Thanks in advance.  I know I'm probably leaving out tons of needed info, but I'm just very frustrated at this point.

---

### Post by dragonfly41 on 2011-03-27
You've just entered the Sargossa Sea of failed XP or Vista installations after installing Ubuntu.

I've got a failed Vista OS to sort out.

The Stop error message is discussed here ..

[http://support.microsoft.com/kb/316401](http://support.microsoft.com/kb/316401)

Are you in an early enough position to start again .. a bit wiser .. reformatting HDD and a fresh installation of Windows in a separate partition from Ubuntu?

---

### Post by gordintoronto on 2011-03-27
We probably are not well qualified to solve Windows problems... That said, I would pretend I had an empty hard drive, and start from scratch, as suggested above.

It's possible XP will not support the graphics on the I3 chip.

---

### Post by oldfred on 2011-03-27
When I installed a new motherboard I turned on AHCI and my XP stopped working. Ubuntu worked either way. 

There may be other BIOS settings that have to be set to some older version to be compatible with XP. 

The windows folks may know more.

You do have to create a primary NTFS partition with the boot flag for windows or have a clean unformated drive.

---

