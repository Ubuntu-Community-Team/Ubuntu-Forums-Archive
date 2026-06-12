---
title: "Freeze problem"
date: 2010-09-24
forum: General Help
---

### Post by Wtower on 2010-09-24
Hello all,

I am in this extremely annoying situation that my pc freezes and nothing can be done but hard reboot. I apologize in advance if this thing is brought up before and for the length of my post. I have found a lot of interesting relevant stuff like [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) and [http://ubuntuforums.org/showthread.php?p=201964](http://ubuntuforums.org/showthread.php?p=201964) but couldn't resolve it.
I am new in Linux and already my main choice of OS.

I have Ubuntu 10.04, fully updated. Runs on an ASUS P5Q (listed in Ubuntu compatible m/b's) with ATI Radeon 4800 (don't know if relevant). In the last week approximately, I have realized that in seemingly random times the system freezes. I am not absolutely sure if this was something that could have happened earlier on, but it just didn't occur. It appears that this started after some update. The interesting part is that it came to my attention that it is 100% certain that will freeze during a file synchronization analysis between usb hdds with Unison (!). This is something I didn't use to do, and of course I have never been able to complete since I have this situation.

After that, two things come to my mind. One is, I wonder why the sync process provokes this, and if has got anything to do with all things said about X freezes, ACPI or hardware acceleration. Second, I wonder how on earth I could locate the relevant updated packages and rollback. You see, last week I remember at least 4-5 updates with 5-10 packages updated. Running through the dpkg log doesn't help me a lot, the list is fairly big, and I believe for a result not exactly guaranteed.

I understand that my information is not sufficient, please advise for anything else needed. Dear community, I kindly ask for your help being stuck on this and not knowing how to get through.

Kind Regards

---

### Post by alchemist330 on 2010-09-24
i have the same problem but mine has an error like the graphics properties arent set right an it jus reboots over an over till i unplug it

---

### Post by Wtower on 2010-09-25
After a long night of no sleep, let me share my findings. I believe that the freeze issue has been caused by 2 situations.

First, the usb drive access. For some reason, the problem stopped after I changed the usb ports of the external hdds from the front panel to the rear side of the case. I can't be sure why, somewhere I read that it might have to do something with bad voltage of a usb hub.

Second, I edited xorg.conf and added the option "RenderAccel" "true". This seemed to have eliminated the random freeze during normal uses.

I hope this will help for future reference. If I have something new I will add up.

Regards

---

### Post by edward1978 on 2010-09-25
It also freezes on me, barely at all, but annoying. 8.04 didn't freeze, but I had trouble with my wireless network with that, so not going back. Ok sorry, anyway no mention of the crash in messages or syslog. Someone told me his system froze also & to disable power management at kernel level. It didn't work for me, like it did for him. Only my mouse freezes though, could it be my mouse. Had SuSE/OpenSuSE for years with the same mouse & no probs. with it. Here are my system specs.

EVGA. nForce 650i ultra Intel Core 2 Duo Wolfdale E8200 2.66GHz 
6MB Cache Dual Core 1333MHz  4 Gig DIMM-DRAM NVIDIA GeForce 8800 GTS with 512 DDR3 memory (PCIe 1.00 x16)

---

### Post by davidvandoren on 2010-09-25
I have the same thing.

motherboard msi h55m-E33
intel R cor Tm i3 5.30 2.93 GHz
msi nvidia N220GT Graphic

with gnome mouse an keyboard freezes.
with KDE I can move the mouse but not click on anything.

Soft reboot with ctrl alt + prtSc and then typing reisub works sometimes.
I suspect the network manager. Don't ask me why but the first crashes I had were during my first update while downloading. 
The other when clicking on the connect Icon. Or scrolling a browser window which isn't fully loaded.

---

### Post by edward1978 on 2010-09-25
> **davidvandoren said:**
> I have the same thing.

motherboard msi h55m-E33
intel R cor Tm i3 5.30 2.93 GHz
msi nvidia N220GT Graphic

with gnome mouse an keyboard freezes.
with KDE I can move the mouse but not click on anything.

Soft reboot with ctrl alt + prtSc and then typing reisub works sometimes.
I suspect the network manager. Don't ask me why but the first crashes I had were during my first update while downloading. 
The other when clicking on the connect Icon. Or scrolling a browser window which isn't fully loaded.

It is annoying, my mouse isn't on the hardware compatible with Ubuntu list, my motherboard isn't also. I have this command someone told me to try pasted in the searchbar in Firefox, but no freezing since I pasted it, so haven't tried yet. My mouse is only frozen, so I am starting to think it might be the mouse. Well never mind just the mouse freezing a few mins ago everything froze. This is really getting annoying, wish I could find 1 clue...

---

### Post by Wtower on 2010-09-25
Bump. Again same thing while running vlc. Too pity so many people face such situations and nothing to be done.

---

### Post by davidvandoren on 2010-09-25
I just stumbled across the bios option  **lan option rom**.
It was disabled by default.
I don't really know what it is for but searching for it on the internet I found that it enables newer operating systems to make full use of its lan. 
There were also some bios bugs reported with this setting.

> I actually got SATA RAID to work in 3.6. It's REALLY buggy for sure! To get the Option Rom for the RAID controller to load, you must enable the option in the BIOS for "Onboard LAN Option ROM". I know, it makes no sense. But it seems by disabling the LAN option rom, as most users would, it actually disables the RAID bios too. 

Even more buggy? When you ENABLE the LAN option rom, to get RAID to work, you LOSE your ability for DOS USB Keyboard support. The option for USB Keyboard goes greyed out. You can actually enable it, but when you go to the next option, it gets disabled and grey'd out again and the setting never "sticks". Hella buggy. Turn OFF the LAN option ROM, and the USB keyboard support works again! But you lose RAID! Arrrggggh!!

On my fedora 13 I always got this crash report mentioning hd audio blabla I forgot. 
However when enabling **lan option rom**I saw something at boot loading with hd audio. 

Also a download which yesterday crashed 4 times went through with no problem now. 680Mb in 7 minutes.

I hope that was the problem here.
keep my fingers crossed

---

### Post by Wtower on 2010-09-26
I added in xorg.conf in section device an option "AccelMethod" "XAA" and it seems to have eliminated the problem. I have completely removed the "RenderAccel" "false" option (I think the default for that is true).

The link I posted above [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) was of great help, I just hadn't understood it properly. It wasn't clear to me what I discovered later on and I will describe for future help.

> Option "AccelMethod" "xxx" - Try "XAA", "EXA" (ignored on -intel > 2.8.0)

The AccelMethod EXA is the default option for my distribution. It is to be a faster method of accelerating graphics, but apparently a fault one in my case. Switching back to XAA, the previous one default one was the solution for my case.

Regards

---

