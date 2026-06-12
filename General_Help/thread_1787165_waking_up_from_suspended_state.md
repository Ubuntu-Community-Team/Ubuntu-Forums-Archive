---
title: "waking up from suspended state"
date: 2011-06-20
forum: General Help
---

### Post by Monotoko on 2011-06-20
I was wondering if there was anyone here who would be kind enough to help me. I dual boot both Windows and Linux and I often put my computer to "sleep" at night so it's easy to wake up the next morning. In Windows I just need to press a few keys and my computer comes to life, in Linux this doesn't happen and I have to actually go for the power button. (This wouldn't be so bad if the computer wasn't in a hard to reach place in a cupboard)

At the moment I have a USB hub which my keyboard and mouse plug into, but for the sake of testing I plugged a second USB keyboard directly into the machine itself, again neither wake it. Doing a bit of research I have discovered that the wakeup devices are stored in /proc/acpi/wakeup

The contents of the file by "cat" are as follows:
```
monotoko@KatieIV:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
PCE2	  S4	*disabled  pci:0000:00:02.0
PCE3	  S4	*disabled  
PCE4	  S4	*disabled  
PCE5	  S4	*disabled  
PCE6	  S4	*disabled  pci:0000:00:06.0
ALAN	  S4	*enabled   pci:0000:02:00.0
PCE7	  S4	*disabled  
PCE9	  S4	*disabled  
PCEA	  S4	*disabled  
PCEB	  S4	*disabled  
PCEC	  S4	*disabled  
SBAZ	  S4	*disabled  pci:0000:00:14.2
UAR1	  S4	*disabled  pnp:00:08
P0PC	  S4	*disabled  pci:0000:00:14.4
UHC1	  S4	*disabled  pci:0000:00:12.0
UHC2	  S4	*disabled  pci:0000:00:12.1
UHC3	  S4	*disabled  pci:0000:00:12.2
USB4	  S4	*disabled  pci:0000:00:13.0
UHC5	  S4	*disabled  pci:0000:00:13.1
UHC6	  S4	*disabled  pci:0000:00:13.2
UHC7	  S4	*disabled  pci:0000:00:14.5

```

and the contents of lspci:
```
monotoko@KatieIV:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0 [COLOR="Red"](DIRECT USB KEYBOARD)[/COLOR]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 0603:00f2 Novatek Microelectronics Corp. [COLOR="Red"](USB HUB KEYBOARD)[/COLOR]
Bus 001 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 003: ID 045e:0770 Microsoft Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

At this point I have reached a dead end, how do I tell the acpi wakeup to accept input from USB keyboard as a kickstart?

---

### Post by pqwoerituytrueiwoq on 2011-06-20
i do not have this issue sleep works fine
although my bios has a option like boot on key press i set it to space (take a look for it)
is this a wireless keyboard?
some computers hate sleep/hibernate like my sisters which does not even power down it just locks up

---

### Post by Monotoko on 2011-06-20
Nope it's a standard keyboard, I figured out that I was looking at /proc all wrong, it isn't a collection of files but an interface between the user and the kernel.
Sending: ```
root@KatieIV:/home/monotoko# echo USB4 > /proc/acpi/wakeup
``` changed the USB4 to "enabled" and now it works.

Odd that it didn't like it out of the box...I think it may be BIOS dependant, I have marked it as solved in the hope someone looking for the same answer stumbles across this one day..

---

