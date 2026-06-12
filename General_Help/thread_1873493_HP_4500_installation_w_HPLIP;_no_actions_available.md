---
title: "HP 4500 installation w/ HPLIP; no actions available"
date: 2011-11-01
forum: General Help
---

### Post by solutionorppt on 2011-11-01
I installed 10.04 on my laptop in a dual boot configuration (Vista) a couple weeks ago.  Ubuntu did a good job detecting and installing drivers for my HP Officejet 4500 All-in-one.  It printed the test page and all subsequent documents perfectly and I thought all was well until I tried to scan a document.  I looked around the forum, and I thought I had found a simple solution...

I installed the drivers from HPLIP via terminal; in the "Device Discovery" process it asks you how you want to detect the device (I/O) and allows you to choose from USB, Network/Ethernet/Wireless, or Wireless/802.11...

I select the last choice and follow the prompts to set up the printer on my wireless network using a temporary USB connection.  After it connects the printer to the network, it tells me to disconnect the USB.  I do this and click "Finish."  It returns me to the "Device Discovery" screen and I am prompted to repeat the process in a rather nasty recursion...

Now I can't even print, let alone scan.  Am I missing the forest for the trees somewhere here?

---

### Post by dino99 on 2011-11-01
use the hplip package from synaptic, it works smootly. So , from synaptic, remove/purge hplip* then reinstall the package from your distro.

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by solutionorppt on 2011-11-01
Okay, I did that and now I can't even detect the printer at all.

Searching on USB bus...
error: No devices found on bus: usb

---

### Post by solutionorppt on 2011-11-01
Sorry, meant to include the output from hp-check -r...

I got a couple errors and a warning:

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Officejet-4500-G510n-z
----------------------
Type: Unknown
Device URI: usb://HP/Officejet%204500%20G510n-z?serial=CN17RK12G605HR
PPD: /etc/cups/ppd/Officejet-4500-G510n-z.ppd
PPD Description: HP Officejet 4500 g510n-z, hpcups 3.11.10
Printer status: printer Officejet-4500-G510n-z is idle.  enabled since Tue 01 Nov 2011 01:32:59 PM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

...


-----------------
| USB I/O SETUP |
-----------------

Checking for permissions of USB attached printers...

HP Device 0x2e12 at 002:004: 
    Device URI: hp:/usb/Officejet_4500_G510n-z?serial=CN17RK12G605HR
error: Unsupported model: Officejet_4500_G510n-z

---------------
| USER GROUPS |
---------------

root

error: User needs to be member of group 'lp' to enable print, scan & fax.
error: User needs to be member of group 'lpadmin' to manage printers.

---

### Post by solutionorppt on 2011-11-01
Okay, I can "see" and print to it using System > Admin > Printing, but this HPLIP POS still can't find it even when it's directly pugged into the USB port.

Searching on USB bus...
error: No devices found on bus: usb
Searching on USB bus...
error: No devices found on bus: usb
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=mdns)
error: No devices found on bus: net


WTF!?!

---

### Post by solutionorppt on 2011-11-01
I suppose it bears mentioning that the HPLIP software is the only thing unable to detedt the printer...

laptop:~$ lsusb
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 03f0:2e12 Hewlett-Packard

---

