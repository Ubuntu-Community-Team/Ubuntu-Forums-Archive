---
title: "Can someone explain procedure for running memtest86 please?"
date: 2011-12-14
forum: General Help
---

### Post by rootessa on 2011-12-14
Reboot your  computer and right after the bois splash tap the shift key. This should  bring up the grub menu and you can select memtest from that menu.
 		                   		  		  		 		 			 				__________________

I found this on another post. I'm not sure what bois splash means. I did  try tapping the shift key on  startup to no avail.
I'm having the same old problem again. Laptop runs fine for months. I install updates from update manager and from there I have the same probs. Crashing, freezing, turning gray. This time it's  been going on for 7 days.
someone suggested I run memtest when I had this problem in Oct.This time overheating isn't an issue. Have thoroughly dusted and have it sitting on 4 boxes of mac and cheese (the best use I've found for the stuff!) :D for air circulation.
I'm stumped once again. Checked system and it says memtest86 is installed.
Anymore suggestions?
thanks!

---

### Post by dFlyer on 2011-12-14
Try rebooting and keeping the shift key pressed once the computer start or after the blank screen on the reboot.

---

### Post by jimmydean886-2 on 2011-12-14
Holding down the shift key is probably the BEST option, but if that fails, start up your computer, and when you get past the BIOS screen, FORCE SHUT DOWN the computer.

WARNING!: This is potentially dangerous, especially during boot. ONLY do this as a last resort if holding the SHIFT key DOESN'T work.

---

### Post by plucky on 2011-12-15
Boot your Live CD and ruin Memtest+86 from there if the other suggestions don't work.

Good Luck

---

### Post by seawolf167 on 2011-12-15
To run memtest86 from hard drive installed version:

[LIST]
[*]hold [SHIFT] during POST (immediately after power on)
[*]at the resulting Grub menu, select the memtest86 entry
[/LIST]
To run memtest86 from a live cd:

[LIST]
[*]download and burn a [Ubuntu live cd]("https://help.ubuntu.com/community/LiveCD#Preparing_your_LiveCD")
[*]either:
[LIST]
[*]set your cd/dvd drive to have a higher boot priority in BIOS than your hard drive
[*]hit the corresponding key (usually [F10] or [F12]) to get a boot menu during POST, then select to boot off the cd
[/LIST]
[*]select the memtest86 entry
[/LIST]

---

### Post by efflandt on 2011-12-15
For some reason memtest86+ does not work from grub2 in 11.10 (I think it said "not enough low memory").  So I didn't even think of trying it from iso on USB.

I simply downloaded the memtext86+ iso, burned it to CD, and that worked.

---

### Post by alecz20 on 2012-03-24
> **seawolf167 said:**
> To run memtest86 from hard drive installed version:

[LIST]
[*]hold [SHIFT] during POST (immediately after power on)
[*]at the resulting Grub menu, select the memtest86 entry
[/LIST]
To run memtest86 from a live cd:

[LIST]
[*]download and burn a [Ubuntu live cd]("https://help.ubuntu.com/community/LiveCD#Preparing_your_LiveCD")
[*]either:
[LIST]
[*]set your cd/dvd drive to have a higher boot priority in BIOS than your hard drive
[*]hit the corresponding key (usually [F10] or [F12]) to get a boot menu during POST, then select to boot off the cd
[/LIST]
[*]select the memtest86 entry
[/LIST]

So I put the live CD, then it boots from CD. But the only options are "Try Ubuntu" and "Install Ubuntu" no more memtest option. Oh, and this is on a nice graphical interface.

Was the memtest removed from Ubuntu Live CD's to make them less versatile?
Now we need a separate memtest86 cd?

---

### Post by Darwood on 2012-10-16
> **alecz20 said:**
> So I put the live CD, then it boots from CD. But the only options are "Try Ubuntu" and "Install Ubuntu" no more memtest option. Oh, and this is on a nice graphical interface.

Was the memtest removed from Ubuntu Live CD's to make them less versatile?
Now we need a separate memtest86 cd?

Hit the tab key during bootup.

---

### Post by ricardisimo on 2013-01-27
I'm running the 64-bit 12.10. No memtest option during boot. Nor is there one on the corresponding LiveCD (wich is a DVD now and no longer a CD, by the way, but whatever...)

Assuming I can just run from the 32-bit version of the LiveCD, can someone guarantee me that it is in fact on there before I download and burn it? Thanks.

Curiously, memtest86+ is clearly installed on my system. Is there no way to run it from a terminal? Boot-level only operation, is it?

---

### Post by Sef on 2013-01-27
> I'm running the 64-bit 12.10. No memtest option during boot. Nor is there one on the corresponding LiveCD (wich is a DVD now and no longer a CD, by the way, but whatever...)


Just go the [MemTest86]("http://memtest86.com/") website and download it, and download it.

---

### Post by alecz20 on 2013-01-27
> **ricardisimo said:**
> I'm running the 64-bit 12.10. No memtest option during boot. Nor is there one on the corresponding LiveCD (wich is a DVD now and no longer a CD, by the way, but whatever...)

...


Not sure about 12.10, but on 12.04 LiveCD, pressing TAB key during boot brings the classical menu with several other options including the memory test option.

Have you tried pressing TAB during boot to see what it gives?
Alternatively you can get a version of Ubuntu 12.04 or older LiveCD which will have that option.

I think that for a 64-bit system you need the 64-bit version.

---

### Post by Yellow Pasque on 2013-01-27
It should be installable from the regular Ubuntu repo, and then you have to reboot and select it from GRUB menu (as mentioned, hold shift to show grub menu).
```
sudo apt-get install memtest86+
```

All the mobos I bought in recent years came with memtest built right into the BIOS, and it could be run by hitting a key at POST screen or going into the BIOS.

---

### Post by ricardisimo on 2013-01-28
No, memtest86+ is already installed on my machine. It's just not apprearing as a boot option. I tried editing etc/default/grub, but that file no longer looks anything like it used to. More Ubuntu wisdom from on high. Whatever. I also tried the memory test from an older kubuntu livecd. No love.

Has anyone tried the related memtester application? How is it run? Do I need to all of the switches and options, or can I just run the defaults?

---

### Post by ricardisimo on 2013-01-30
The 32-bit ("normal") version of 12.10 had it on the LiveCD. Memory was way bad. Got it solved. Thanks to all.

---

