---
title: "Pulling out of hibernate boots into Windows"
date: 2010-08-04
forum: General Help
---

### Post by UncleNinja on 2010-08-04
Hi Ubuntu people! :D

I've recently swapped from Windows 7 to Ubuntu Lucid Lynx and I haven't looked back - except for the fact that moving from Photoshop to GIMP is difficult. :-|
I digress.

Suspend works nicely (what a blessing :D) but Hibernate doesn't. 

Ubuntu 10.04 is installed on a 500GB Seagate External hard drive plugged into a USB port on my motherboard. My BIOS is set to boot off of it automatically (boot order). 
Windows 7 is installed on my 160GB (:frown:) internal drive.

The problem is not when I put it into Hibernate, it's when I pull it out of hibernate. When I do my computer tries to unhibernate into Windows! Doh! :o

My hardware ($300 laptop from Walmart haha) - [click here for more info on HP's site if you want]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01753032")

**Model:** Compaq Presario CQ60-419-wm
**Video Card:** Nvidia GeForce 8200M G
**Processor:** AMD Sempron (:frown:) 2.1 GhZ
**RAM:** 3GB
**OS it was shipped with:** Vista Basic (:frown:)

[SIZE="2"]Is there some BIOS setting to fix this or something?[/SIZE]

Thanks! 
:guitar:

---

### Post by floorish on 2010-08-04
So, you're in Ubuntu -> hibernate -> start pc -> pc tries to start Windows instead of Ubuntu, right?

I'm not an experienced Ubuntu user, but I like to hibernate and switch to windows, so I can easily switch back to Ubuntu.
This is what I did:
- install uswsusp: sudo apt-get install uswsusp (kind of hibernation program)
- edit /etc/uswsusp.conf to your liking (check 'resume device')
- hibernate: sudo s2disk

Note: I did this because I want to reboot after hibernate, so I can switch OS. Not sure if this will help you, but it works for me ;) However normal hibernation worked as well...

---

### Post by UncleNinja on 2010-08-04
> **floorish said:**
> So, you're in Ubuntu -> hibernate -> start pc -> pc tries to start Windows instead of Ubuntu, right?

I'm not an experienced Ubuntu user, but I like to hibernate and switch to windows, so I can easily switch back to Ubuntu.
This is what I did:
- install uswsusp: sudo apt-get install uswsusp (kind of hibernation program)
- edit /etc/uswsusp.conf to your liking (check 'resume device')
- hibernate: sudo s2disk

Note: I did this because I want to reboot after hibernate, so I can switch OS. Not sure if this will help you, but it works for me ;) However normal hibernation worked as well...
So with that application the BIOS will follow the boot order upon coming out of hibernate? Looks cool, I'll look into it. :)

Thanks for replying :KS

---

### Post by floorish on 2010-08-04
I'm not sure, but it has a 'resume device' option, so you could try and uninstall if it doesn't work. But maybe your bios just likes Windows too much :p

---

### Post by btindie on 2010-08-04
When a Linux computer hibernates it stores the memory contents to the swap partition. When you turn it back on, and if it boots to the Linux partition it should recognise the fact and resume.
 
I can only think that for what ever reason your computer is booting from the internal hard disk. After a hibernate, try selecting the required boot device from the BIOS setup. i.e. if you tell the BIOS to boot your external disk then power off normally, when you then turn it on again will it boot the external disk without any intervention?
 
Or have you got Windows to to multi boot into Linux?

---

### Post by UncleNinja on 2010-08-04
> **btindie said:**
> When a Linux computer hibernates it stores the memory contents to the swap partition. When you turn it back on, and if it boots to the Linux partition it should recognise the fact and resume.Handy to know :D
> **btindie said:**
> Or have you got Windows to to multi boot into Linux?Kinda. Windows has no clue that Ubuntu even exists. However, my BIOS's boot order dictates that it should boot off of my external hard drive (the one that has Ubuntu on it) first.
> **btindie said:**
> I can only think that for what ever reason your computer is booting from the internal hard disk. After a hibernate, try selecting the required boot device from the BIOS setup. i.e. if you tell the BIOS to boot your external disk then power off normally, when you then turn it on again will it boot the external disk without any intervention?Yup, that's exactly what's happening. 
It's odd - normally when I boot normally (i.e. after a shutdown) it shows the Compaq logo and below a bunch of text telling you which buttons to press to do what - you know the drill.
Yet when I boot back up after hibernating it just shows the Compaq logo and nothing else. hmm....

If I mash F9 (the key for choosing the device to boot off of, at least with my BIOS) after hibernating nothing happens - it just boots into windows. If, while it's doing that, I press F9 it will ask me if I want to boot in recovery mode and all that jazz. 
If I hold the power button the computer shuts off (obviously :)). Then when I turn it back on it works normally.

I'm going to shut down and examine my BIOS settings in case there's some "feature" causing this to happen. If I don't find anything I'll try out your idea, floorish. :)

Thanks! You guys reply so fast that this feels like a chat room! :KS

---

### Post by badbradmx on 2010-08-04
maybe because the swap file is on the external? may not make a difference just an idea

---

### Post by UncleNinja on 2010-08-04
Explored my BIOS settings and didn't find anything useful.

I wonder if my BIOS is hard-coded to boot off the internal drive after being pulled out of hibernate. hmm.. :-k

:KS

---

### Post by btindie on 2010-08-04
After hibernating try going into the BIOS boot options and seeing what the boot order is.
 
The memory contents is saved to the swap file, so after initrd is loaded it mounts the root partition with that reading /etc/fstab then from that getting the UUID of the partition that contains swap. So you'd have thought it'd know that that was a hibernated partition and should resume. Have you tried unpluging the internal hard disk to see that it resumes correctly?
 
I think when the system goes into hibernate it should save the contents of RAM to swap then power of the system. So when you power it on it should be the same as if it was a cold start to the system. Unlike suspend to ram (S3) where the program state is saved to RAM and continues from the point it left off.

---

### Post by UncleNinja on 2010-08-04
*Note: sorry, I'm not trying to disrespect your ideas, I'm just hesitant to try some of that stuff and some of it is impossible (thanks a lot, HP! :evil:).*
> **btindie said:**
> After hibernating try going into the BIOS boot options and seeing what the boot order is.
It won't let me for some reason. I am unable to press F10 to enter the BIOS settings. 
 
[QUOTE=btindie]The memory contents is saved to the swap file, so after initrd is loaded it mounts the root partition with that reading /etc/fstab then from that getting the UUID of the partition that contains swap. So you'd have thought it'd know that that was a hibernated partition and should resume. Have you tried unpluging the internal hard disk to see that it resumes correctly?[/QUOTE]I would, but it's a laptop and I'm a bit nervous about opening the case and unplugging stuff. :)
If all else fails I'll probably just try this. :D 

[QUOTE=btindie]I think when the system goes into hibernate it should save the contents of RAM to swap then power of the system. So when you power it on it should be the same as if it was a cold start to the system. Unlike suspend to ram (S3) where the program state is saved to RAM and continues from the point it left off.[/QUOTE]
I'm stumped as to how the computer knows that I just went into hibernate! :o It's magic or something!

Basically GRUB is completely ignored and the systems boots right off of my Internal disk and uses the Windows bootloader. :o

Thanks for replying! (no sarcasm intended) :KS

---

### Post by badbradmx on 2010-08-05
most laptops have a separate removed flap on the bottom to change the drive easily. or a couple of screws allowing the hard drive to then slide out the side

---

### Post by UncleNinja on 2010-08-11
I basically just reinstalled Ubuntu and put the GRUB bootloader on my internal drive. 
Now when I pull out of Hibernate it unhibernates properly (into Ubuntu and restores my session)! YAY! :D

P.S.: how do I mark this thread as solved? Did I do it right? :)

---

### Post by interdist on 2011-03-11
I am having the same problem. Ubuntu Maverick (10.10) was installed using Wubi from within Windows 7. It also installed a boot manager, probably not grub.

Now, after I hibernate Windows and power the computer up, it will always go on and load Windows, without allowing any of the F-keys (just as described in this thread).

Any suggestions?

---

### Post by btindie on 2011-03-14
I think your problem is different to the one originally posted about, you'd be better off starting your own thread.

The problem I think is with windows as when it's been hibernated it will only let you resume from hibernation and not give you the option to boot another partition. I'm not familiar with a WUBI install but I'm guessing that windows is still being used as the boot manager on the MBR. If the windows boot manager is in charge then I don't think it's possible to boot another OS if windows has been hibernated.

---

### Post by Kixtosh on 2011-04-05
> **btindie said:**
> ... I'm not familiar with a WUBI install but I'm guessing that windows is still being used as the boot manager on the MBR. If the windows boot manager is in charge then I don't think it's possible to boot another OS if windows has been hibernated.Windows still being used as the boot manager may be the problem here, as you suggest. I dual boot on several laptops, but I installed normally (not with WUBI), so i get a GRUB menu when starting up. I can:

1) From Ubuntu, hibernate,
2) Start and, from GRUB, select Windows,
3) Hibernate Windows,
4) From GRUB choose to resume either Windows or Ubuntu freely.

Basically, I can have both O.S.'s in hibernation at the same time, and start whichever I please, depending on which one I select from GRUB. I mostly don't bother, though, since Ubuntu is too slow to hibernate in the first place on my laptops, and very much faster to shut down. It only saves me 10-15 seconds to resume from hibernation instead of starting Ubuntu normally. It's much the same story with Win XP or Vista. Windows 7 does hibernate just about as fast as it shuts down, however, and it resumes from hibernation much faster than it starts up (but neither is nearly as fast as Ubuntu shutting down and starting up normally on my laptops). Basically, as far as hibernation goes, this is the only area where I have noticed Win 7 being better than Ubuntu at anything I currently use.

---

