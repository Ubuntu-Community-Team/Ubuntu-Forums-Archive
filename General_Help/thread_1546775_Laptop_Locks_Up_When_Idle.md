---
title: "Laptop Locks Up When Idle"
date: 2010-08-05
forum: General Help
---

### Post by Maverick_Meerkat on 2010-08-05
Greetings all,

I'm having a minor (but annoying) problem with Ubuntu 10.04. If I leave the computer set idle for exactly 11 minutes, the darn thing locks up. The only method to get it working again is to turn the machine off and reboot.

Some info you might want to know:

Toshiba Satellite A55-S106
Intel Celeron M-360 1.4 GHz
1Gig RAM
Intel 852GM ChipSet

Steps taken to correct problem:

CPU
- is not overheating
- is properly seated

RAM
- is properly seated
- is not faulty or defective

BIOS
- changing power settings has no effect

Grub
- adding acpi=off to grub config has no effect

Screen Saver
- disabled in settings
- disabled in Startup Applications
- removed via Synaptic Package Manager

Power Management
- is set to put computer to sleep: never
- when laptop lid is closed: blank screen
- put display to sleep: never
- dim display when idle checkbox is: NOT marked
- is not set to hibernate
- is not set to suspend
- is not set to spin down disk

Advanced Power Management
- is not set to Lock Screen on hibernate
- is not set to Lock Screen on suspend
- is not set to Lock Screen on blank screen

APCI
- disabled in Startup Applications
- disabled via sysv-rc-conf
- removed via Synaptic Package Manager

Network
- online/offline has no effect

Conky
- running/not running has no effect

OS
- does not occur when I boot to XP Pro 

What else am I missing? Any ideas on what is causing the lock up to occur? Any suggestions on how to resolve the problem?

---

### Post by Maverick_Meerkat on 2010-08-06
61 views and not one response. Certainly, there must be one person who has a suggestion.

---

### Post by n8nt on 2010-08-06
Hi,
I just installed 10.04 desktop over top of my o.d 8.06 version and it won't run more than 5 minutes before locking up. I had first installed the server version but forgot it did not have a GUI so went back and installed the desktop. I have a 64-bit machine so I'm going to try and install the 64-bit version.
 
I hope you get an answer.

---

### Post by Maverick_Meerkat on 2010-08-07
UPDATE:

This problem must be graphics/video related. I just discovered that while watching streaming video at the 11 minute mark the display locks up and stops responding as usual. However, sound continues to stream and play without interruption. 

Although, there is and odd exception. When I play MP3's (stored on a separate mounted partition) using Banshee, it plays all night and doesn't lockup. This doesn't make any sense to me at all.

I'll have to scour the net some more looking for answers, but if anyone has any suggestions at all, please let me know. Heck, I'll try anything!!! I have the system backed up. So if I really screw the pooch, it's no big deal.
:D

---

### Post by Maverick_Meerkat on 2010-08-07
UPDATE:

I discovered this is definitely NOT a bug. IT WAS A USER CREATED PROBLEM! 

When I cleaned and optimized the OS, I mess around in places I shouldn't. Resultantly, I inadvertently deleted files I should not have!

REMEDY:

Re-installed OS, which obviously replaced whatever files were missing.

Note: 

I have been more prudent when cleaning and optimizing this time. Complete testing has proven the issue to be resolved.

---

### Post by nwallhausen on 2010-10-17
I had the same type of problem with my desktop installing ultimate edition 2.7 It cleared up once I activated the restricted graphics driver and rebooted :)

---

