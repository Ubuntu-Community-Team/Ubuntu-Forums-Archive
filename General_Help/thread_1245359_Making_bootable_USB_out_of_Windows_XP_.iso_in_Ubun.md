---
title: "Making bootable USB out of Windows XP .iso in Ubuntu"
date: 2009-08-20
forum: General Help
---

### Post by pyedog on 2009-08-20
Hi everyone, this might sound like a Windows problem but it's not. My brother has an Acer Aspire One with Linpus on it, he's not very good with computers though and he wants the familiarity of Windows etc. I have acquired a copy of XP - legitimate of course ;o) - but the Acer has no optical drive so i need to get this .iso to boot from a pen drive ideally.

I got a little frustrated with the fact that every time I booted my own Windows system it started downloading and installing another 300MB of 'critical updates' before asking me to restart my machine over and over. As such, my machine is now Linux-only. Does anyone know of an easy way, using Ubuntu, to get the bootable Windows .iso onto a bootable USB drive so I can install it on my brother's system?

Cheers :)

---

### Post by matthewbpt on 2009-08-20
Don't think that's possible with windows, you will have to use an external usb optical drive and an xp cd to install it. I suggest you do a google search to find a solution.

---

### Post by pyedog on 2009-08-20
I wouldn't post in a support forum with doing a google search first, lol.

It is possible, but the tools that I have found to do it (eg tools to make a USB drive bootable etc) are all Windows based. I was wondering if I can do it through Ubuntu since I don't have access to a Windows machine right now.

I was thinking of using gparted to set the boot flag on the usb partition, then mounting the .iso and copying all files over. This sounds a bit to easy though, I assume that there's more to it?

---

### Post by Penguin Guy on 2009-08-20
I am not 100% sure, but perhaps you should try [COLOR="Green"]System -> Administration -> USB Startup Disk Creator[/COLOR]. USB Startup Disk Creator allows you to put a .iso on a USB sick and make it bootable - that might just do what you want.

---

### Post by nmaster on 2009-08-20
Why can't you use "USB Startup Disk Creator" within System->Administration?

---

### Post by pyedog on 2009-08-20
Because I'm not creating an Ubuntu startup disk. I want to create a Windows startup disk using the Windows .iso from within Ubuntu.

---

### Post by pyedog on 2009-08-20
My mistake, I didn't realise I can make a startup disk from a .iso using that tool. Thanks for your help, I'll give it a try.

---

### Post by pyedog on 2009-08-20
The USB Startup Disk creator tells me "This is not a desktop install CD and thus cannot be used by this application." when I select the .iso file.

---

### Post by matthewbpt on 2009-08-20
Thats because it can only make linux startup disks using casper. That tool is useless for windows disks.

---

### Post by pyedog on 2009-08-20
Yes, I was under the impression that was the case. I was pretty sure it was a tool for making Linux boot disks but I thought I'd give it a go. I'll try my original gparted plan tomorrow but I'm pretty sure that's gonna fail as I'm not really familiar with the file structure of bootable disks. Thanks anyway.

---

### Post by oldfred on 2009-08-20
I made this comment on another thread, but have not tried this with XP:

Years ago we used a dos disk to partition a drive, formated the drive, a sys command to make the drive bootable , and copied all the windows install to c:\windows\install. Then when it wanted drivers it would default to that directory instead of asking for the install CD. Now adays with the Internet required for just about anything I do not know if you can do that.

Someone else doing the same thing:
[http://ask.metafilter.com/77036/Installing-windows-from-external-hard-drive](http://ask.metafilter.com/77036/Installing-windows-from-external-hard-drive)

You need to make a primary partition, format the drive and make it bootable. If you copy the i386 folder to your c: drive you should be able to bootstrap install. For XP, another site said an old windows 98 diskette would work as the boot is the same.

---

### Post by edwardtilbury on 2009-08-27
this would be very useful for bios upgrades that only work under windows.

---

### Post by Fracta on 2010-10-30
I have a very similar problem. Trying to reinstall windows on a pc and it won't boot windows cds (will boot ubuntu but that doesn't help). I also tried taking out hd, putting it into other pc, installing windows there and replacing hd and it still won't boot into windows. I have isos of xp on my pc (i'm running ubuntu) and I am trying to make a bootable windows xp on a usb stick because thats the only way I can think of now to get windows working. And Startup Disk Creator doesn't work and I can't find anything else that tells me how to do it. Any ideas? And no the pc isn't mine, its for a mate, and yes he definitely wants windows.

---

### Post by macem29 on 2010-10-30
read a bit and it appears this works with windows,
although the description is for linux ISO's, won't hurt to give it a go

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by motersho on 2010-10-30
Try Unetbootin.  [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") 

I use this to create a bootable usb stick from a Windows 7 ISO,  see here ( [http://goo.gl/eUs6]("http://goo.gl/eUs6") ) therefore I am sure that you can do it with an xp disk also.

---

### Post by Fracta on 2010-10-31
thanks! that seemed to work but the pc is so crap it hangs on "Attempting to boot from USB Drive."
At least now I won't be wasting tons of dvds, and I don't have to boot into windows.

---

