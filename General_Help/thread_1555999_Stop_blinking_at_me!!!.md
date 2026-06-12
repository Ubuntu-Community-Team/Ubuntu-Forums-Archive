---
title: "Stop blinking at me!!!"
date: 2010-08-18
forum: General Help
---

### Post by chips24 on 2010-08-18
Hey, I have reinstalled Ubuntu 10.04 several times, and evertime I reboot and try to log on, it just has a white curser blinking at me. I didnt see any errors during the installation so I dont see why it happens. Does anyone have any suggestions?

---

### Post by wilee-nilee on 2010-08-18
Boot a live cd and post
```
**sudo fdisk -l**     l=small L
```

You also have a f6 key option for modes at startup you might try nomodeset, hit ctrl-x to boot from there I think.

---

### Post by chips24 on 2010-08-18
F6 doesnt do anything.

maybe i need more detailed instructions please. thankyou.

---

### Post by chips24 on 2010-08-18
ok, so i went into the Live cd and punched in the commands. However when i restarted the system, it just did the same thing... blank screen and blinking curser...

---

### Post by wilee-nilee on 2010-08-18
> **chips24 said:**
> ok, so i went into the Live cd and punched in the commands. However when i restarted the system, it just did the same thing... blank screen and blinking curser...

The command was to show the partitions and for you to post them.

Can you boot the live cd open gparted take a screenshot of it and post that.

I am trying to figure out what is actually on the HD.

---

### Post by chips24 on 2010-08-18
i managed to start the os after some searching, holding down shift worked and it started up, so here is my disk information, it is incomplete because i do not have a internet connection yet because i need to install drivers-  so i hand wrote it...


Disk /dev/sda: 160.0 GB 160041885096 bytes
255 heads, 63 sectors/track, 19457 cylinders
units = cylinders of 16065 * 512 = 822528 bytes
sector size (logical / physical ): 512 bytes / 512 bytes
I/O size (min/opt): 512 bytes / 512 bytes
Disk Identifier: 0x90db3993

    Device boot     start       end
/dev/sda1            1           1306
/dev/sda2            1307      6932
/dev/sda3            6932      19458
/dev/sda4            6932      19087
/dev/sda5            19087    19458



sorry about the gap, hope this is enough info.

---

### Post by oldos2er on 2010-08-18
If you really only have 99MB RAM, I'd say that's one possible cause of your problem.

---

### Post by chips24 on 2010-08-18
> **oldos2er said:**
> If you really only have 99MB RAM, I'd say that's one possible cause of your problem.

Ubuntu only requires 512 MB.

---

### Post by kbless7 on 2010-08-18
> **chips24 said:**
> ubuntu only requires 512 mb.

99 < 512

---

### Post by chips24 on 2010-08-18
sorry, i meant 0.99GB

---

### Post by chips24 on 2010-08-18
well, i tried the shift thing again, and it wont start it again, it doesnt even go into the loading screen. how come it works ok on the live cd, but it just crashes on its own? i made sure it installed ok, there were no errors except for my wireless drivers- that i needed to update them- but it was fine...

sould i erase the partition and load an earlier version of the os?

---

### Post by oldos2er on 2010-08-18
What video card do you have?

---

### Post by wilee-nilee on 2010-08-18
When you use shift you should be at grub hit e and use the arrow keys to navigate to the end of the kernel and remove nomodset and no splash, hit crtl-x, it may work.

To identify the graphics in the terminal.
```
lspci | grep VGA
```

This sounds like a graphics problem but without more detail it is hard to tell.

---

### Post by chips24 on 2010-08-18
sorry, im actually using xp... here is graphics information

Intel(R) Graphics Media Accelerator Driver for Mobile Report


Report Date:        08/18/2010
Report Time[hr:mm:ss]:    10:44:10
Driver Version:        6.14.10.4926
Operating System:        Windows XP* Home Edition, Service Pack 3 (5.1.2600)
Default Language:        English
DirectX* Version:        9.0
Physical Memory:        1013 MB
Minimum Graphics Memory:    8 MB
Maximum Graphics Memory:    224 MB
Graphics Memory in Use:    8 MB
Processor:        x86 family 6 Model 28 Stepping 2
Processor Speed:        1596 MHZ
Vendor ID:        8086
Device ID:        27AE
Device Revision:        03


*   Accelerator Information   *

Accelerator in Use:        Mobile Intel(R) 945 Express Chipset Family
Video BIOS:        1585.0
Current Graphics Mode:    1024 by 600 True Color (60 Hz)



*   Devices Connected to the Graphics Accelerator   *


Active Notebook Displays: 1


*   Notebook   *

Monitor Name:        Plug and Play Monitor
Display Type:        Digital
Gamma Value:        2.20
DDC2 Protocol:        Supported
Maximum Image Size:    Horizontal: Not Available
            Vertical:   Not Available
Monitor Supported Modes:
1024 by 600 (60 Hz)

---

### Post by chips24 on 2010-08-18
ok, well none of the commands worked, if i cant find something soon, i am going to delete the partition.

---

### Post by TNT1 on 2010-08-19
Did you try the "nomodeset" switch when booting?

---

### Post by chips24 on 2010-08-19
was it in the commands under edit? if it was, i didnt see any. and F6 didnt do anything. im keeping it for one more day, and if its not resolved, im sticking with widows xp.

btw, if i dont get this resolved, how do i remove the partition, restore bootstrap and get windows to boot up properly without a disk drive?

---

### Post by chips24 on 2010-08-19
i should probably also mention that the computer get very quiet after i select the OS, this doesnt happen when i boot XP. should i use an earlier version of ubuntu?

i tried using 8.04, but it had trouble mounting disks.

and like i said, 10.04 doesnt even get into the loading screen, it just starts a blinking curser after i select the os.

---

### Post by chips24 on 2010-08-19
Its really weird, it boots sometime, but sometimes not. 
please, can you explain in detail to me what you mean by the nomodeset?
I dont understand where where and how to edit this command.

---

### Post by FahadMKS on 2010-08-19
> **oldos2er said:**
> If you really only have 99MB RAM, I'd say that's one possible cause of your problem.


It seems that the Ram itself is the problem.

---

### Post by chips24 on 2010-08-19
dude, i said i made a mistake, it was 0.99 GB.

---

### Post by chips24 on 2010-08-20
Ok, obviously i havnt given enough information. 

I installed Ubuntu 8.04 a couple days ago, but i couldnt mount any af my drives. 

Ubuntu 10.04 booted into the live cd fine and installed with no errors.

However, It only boots on the hard disk periodically.

and i do not have 99mb i have 1 gb.

sometimes it takes me 20 minutes to an hour to restart it over and over again until it gets to the loading screen.

---

### Post by M4he on 2010-08-20
> **chips24 said:**
> sometimes it takes me 20 minutes to an hour to restart it over and over again until it gets to the loading screen.
Does it boot up successfully when it happens to get to the loading screen?

Judging from your hardware info you're using a notebook. Does it have wireless built-in? I had similar problems with my netbook because the default driver for my wireless chipset was mismatching with the chip. It took many restart attempts to boot successfully, otherwise it only displayed that blinking cursor.
The only way to solve that was to connect it to the Internet via LAN (after a successful boot) and go to System -> Administration -> Hardware Drivers and then install the proprietary wireless driver for my chip (which was called "STA"). After that the error never happened again. Maybe this helps you.

Good luck!

---

### Post by chips24 on 2010-08-20
> **M4he said:**
> Does it boot up successfully when it happens to get to the loading screen?

Judging from your hardware info you're using a notebook. Does it have wireless built-in? I had similar problems with my netbook because the default driver for my wireless chipset was mismatching with the chip. It took many restart attempts to boot successfully, otherwise it only displayed that blinking cursor.
The only way to solve that was to connect it to the Internet via LAN (after a successful boot) and go to System -> Administration -> Hardware Drivers and then install the proprietary wireless driver for my chip (which was called "STA"). After that the error never happened again. Maybe this helps you.

Good luck!

it has a broadcom driver....

wow, thats exactly my problem. I guess i just need to find a LAN cable so i can connect my laptop to my Internet. really, thanks!!

---

### Post by chips24 on 2010-08-22
I managed to update my drivers and it starts up without any problems.

Thankyou, sorry you had to put up with my... moments. XD

---

