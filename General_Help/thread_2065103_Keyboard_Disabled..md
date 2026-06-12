---
title: "Keyboard Disabled."
date: 2012-10-01
forum: General Help
---

### Post by TheMophead on 2012-10-01
Hello, 
 
After using other Linux Distros a couple of years ago, I decided to Dual Boot my Desktop and Laptop with Ubuntu and Windows 7.
 
The installation went perfect and everything is installed.
 
However I have one issue. Every now and then, when I execute an application that uses a considerable ammount of CPU, my keyboard is Disabled. I've tried reinserting the USB Keyboard and even inserting another Keyboard. I have this issue also on my Laptop that has the exact same Ubuntu Version on :(
 
Ubuntu Version: Ubuntu 12.04.1 LTS 
 
Any help would be appreciated!

---

### Post by shreepads on 2012-10-01
USB 2.0 depends on the CPU polling the USB interface constantly... If the CPU is too busy to do that then the USB interface will be unresponsive...

Does the system have a PS/2 port?

---

### Post by TheMophead on 2012-10-01
> **shreepads said:**
> USB 2.0 depends on the CPU polling the USB interface constantly... If the CPU is too busy to do that then the USB interface will be unresponsive...

Does the system have a PS/2 port?

The Desktop has a PS2 Port. I hunted for a PS2 Keyboard that works but the same thing happens with the keyboard. I've noticed I'm still able to use certain keys such as Caps Lock, Num Lock etc but the general input keys are unresponsive.

CPU Usage usually is at about  60% When this happens so I personally doubt that this is the problem.

Maybe 12.04.1 is unstable and this is a bug? Should I format this partition and install 12.04? Or should I just wait till an update comes out for this current Version?

---

### Post by Jaylester on 2012-10-01
I have the same problem with my Toshiba Satellite laptop with Win 7 on boot-up.  The keyboard usually functions after a reboot. I have not had the key board become inactive loading a program. I keep looking for some setting I have accidentally changed.

---

### Post by shreepads on 2012-10-03
> **TheMophead said:**
> Maybe 12.04.1 is unstable and this is a bug? Should I format this partition and install 12.04? Or should I just wait till an update comes out for this current Version?

12.04.1 is just 12.04 with all the patches since deployed. If you install 12.04 and run Update Manager, you will get to 12.04.1.

What graphics card and graphics driver are you using? Maybe if you can post the full system specs as well...

---

### Post by TheMophead on 2012-10-03
> **shreepads said:**
> 12.04.1 is just 12.04 with all the patches since deployed. If you install 12.04 and run Update Manager, you will get to 12.04.1.

What graphics card and graphics driver are you using? Maybe if you can post the full system specs as well...

Ok, heres the Specifications as displayed under "Details".

**Laptop Specifications:**

Memory: 4GiB
Processor: AMD Sempron(tm) M100
Graphics: ATI Radeon HD 4200
OS Type: 64-bit
Disk: 123GB

Graphics Drivers: fglrx


**Desktop Specifications:**

Memory: 12GiB
Processor: Intel® Core i7-3770K 
Graphics: NVIDIA GeForce GTX 550Ti
OS Type: 64-bit
Disk: 1.5TB

Graphics Drivers: NVIDIA Drivers that came with the Card on a Disc.

---

