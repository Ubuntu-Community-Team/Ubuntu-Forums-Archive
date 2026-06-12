---
title: "Need help with random kernel panics"
date: 2009-12-10
forum: General Help
---

### Post by 0xABC123 on 2009-12-10
This is a rather long story.

I was installing Xubuntu 9.10 with a LiveCD. In the middle of the installation a kernel panic occured (crash and blinking capslock+scroll lock). I shut down the computer and restarted.

BIOS crashed. I shut it down, waited for 20 minutes, and booted up. No crash this time.

BIOS settings were reseted to defaults (how is that possible?). Since then, the PC has printed something like this at every bootup (can't remember exactly):
> 
FastTrack (tm) 1995-2001 Copyright .....
...
Scanning for IDE devices........ (computer waits for 15 seconds)

No array is found!

Press Ctrl+F to enter setup, Esc to continue booting

(continues booting after 10 second timeout)
If I press Ctrl+F, it shows a menu like this (I can't remember much of it):
> 
Choose an option:

[LIST]
[*]1: auto setup
[*]2: ????
[*]3: Read array
[*]4: ????
[*]5: Configure setup array something
[/LIST]

No matter which option I choose, it just reboots without giving me any feedback/menus and scans for IDE devices over again.


If I let it continue booting, GRUB showed up and crashed with error 15. (xubuntu livecd crashed while installing so it didn't work, obviously)

I rebooted, inserted Xubuntu 9.10 LiveCD and selected "Try xubuntu without any change to your computer". Got kernel panic right after X server started and cursor showed up.

I rebooted, and tried the LiveCD a couple times. Kernel panic every time.


I burned Xubuntu 9.04 LiveCD with my fully working laptop, and rebooted the broken pc with the liveCD.

This time there was no kernel panic. I managed to install a working Xubuntu 9.04 system to hard disk.

I rebooted, it scanned for IDE devices, grub showed up, and the system booted up.


Great! I chose to install the updates. In the middle of downloading packages stage a kernel panic occured, so I rebooted.

The system booted up normally. I chose to install the updates again. This time, a kernel panic came when installing the updates.


Now, it gets past BIOS and GRUB but drops me to "initramfs" command line and reports lots of errors. (probably because it crashed before updates were completely installed)


So.... Why does BIOS act weird? How to fix these kernel panics? I want to reinstall Xubuntu but I don't do it yet because I'm scared of kernel panics.

The 7 years old hardware:
> 
Processor: AMD Athlon XP 2000+
RAM: 256Mb
Hard disk: 82.3Gb
GPU: Nvidia GeForce Ti 4200
Mobo: KT3 Ultra
It's not overheating because in BIOS it shows 35 degrees hot. (the pc has ran 80 degrees hot and worked fine with win98) (stupid smilies)

---

### Post by Yvan300 on 2009-12-10
Why don't you update your bios. I mean your pc is 7 years old man and the problems you are describing don't look like they are related to ubuntu. Also it may be a sign of some of your hardware failing. Just my 2 cents.

---

### Post by Kevbert on 2009-12-10
Please run memtest86+ from the boot menu for a couple of passes. You shouldn't get any errors.

---

### Post by 0xABC123 on 2009-12-10
> **Yvan300 said:**
> Why don't you update your bios. I mean your pc is 7 years old man and the problems you are describing don't look like they are related to ubuntu. Also it may be a sign of some of your hardware failing. Just my 2 cents.

> **Kevbert said:**
> Please run memtest86+ from the boot menu for a couple of passes. You shouldn't get any errors.

MemTest86+ doesn't give any errors. (no kernel panics either)

How am I supposed to update the BIOS when MSI gives only a windows exe? :-?

[http://eu.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=497](http://eu.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=497)

---

### Post by QIII on 2009-12-10
Since you eliminated memory, and I doubt that you would generally get a kernel panic using the LiveCD on a functioning machine, I have to wonder about your processor or MOBO components like capacitors.

You said it ran up to 80 degrees under Windows.

For how long and how often?

The "Max operating temperature" of your processor as given by the OEM is usually the point at which your CPU spontaneously erupts into flames, sets off your fire alarm and sends you to the computer store to buy ... wait for it ... a new CPU because you ran it too hot for too long.

80 degrees is hot.  I get concerned approaching 50.  I've set my fans to kick in at 45.

If you scorched your CPU, you won't get anything to work.

But, you can try this:

Unbutton the case.  Blow out the dust bunnies.  Then, following your OEM's service instructions, CAREFULLY remove your CPU from the socket.  If the thermal compound is baked solid, you are probably SOL.  But maybe not.  Clean the old compound off (CAREFULLY) and replace it with fresh compound.  Replace the CPU and button the case back up.  Try to run it.

But I suspect, unfortunately, that you are beyond that point.

---

### Post by 0xABC123 on 2009-12-11
I reinstalled Xubuntu 9.04 from LiveCD to hard disk. It boots up, X server & XFCE works, mouse & keyboard works, everything works.

But BIOS is acting weird and I keep getting random kernel panics. There are no error messages when kernel panic comes.


When I turn on the PC, the usual BIOS text shows up (do you want me to write down that too?), and then it shows this:
```

MBFastTrack133 (tm) "Lite" BIOS Version 2.00.1.22
(c) 1995-2001 Promise Technology, Inc. All rights reserved.

Scanning for IDE devices.............

No Array is defined.......................................

Press <Ctrl+F> to enter FastBuild (tm) Utility or
Press <ESC> to continue booting..._

```If I press ESC, it keeps going, GRUB shows up, and Xubuntu starts.

If I press Ctrl+F, this menu shows up:
```

FastBuild (tm) Utility 1.32 (c) 1996-2001 Promise Technology, Inc.

============================[Main Menu]===============================

        Auto setup....................[ 1 ]

        View Drive Assignments........[ 2 ]

        View Array....................[ 3 ]

        No disk is found. Please check the
        power and data cable connection. 
        <Press Any Key to Exit>

        Controller Configuration......[ 6 ]


=========================[Keys Available]============================

Press 1..6 to Select Option                           [ESC] Exit

```If I press 1, 2, 3 or 6, it reboots. If I press any other key, it reboots.

It does the above things at every reboot. It didn't do that before. How can I disable that "fasttrack" utility? It seems to be the root of all problems.

Once when I was using xubuntu, it just suddenly closed linux/xubuntu and showed me that fasttrack thing.


I don't think it's a hardware failure. BIOS is just messed up. Do you think that removing and re-inserting CMOS battery can fix the BIOS?

---

### Post by BobSongs on 2009-12-11
[SIZE=3][COLOR=DimGray]**hot processor**[/COLOR][/SIZE]
I would tend to agree with QIII: things may well be hot inside your PC. I would recommend getting a can of compressed air. Blowing with the mouth is bad for several reasons:

[LIST]
[*] it is deceptive (your breath is only so strong, while you may have done all you can, you can never match the power of canned air to eliminate clogged dust)
[*] it is dirty (do you really want to breath that crap in? Bring your PC to well ventilated place and used that compressed air.)
[/LIST]
 Heat often provokes Kernel panics. So, consider the inside of your PC before you consider the issue lies with the O/S, and this is true whether it is Linux **or** Windows.

---

