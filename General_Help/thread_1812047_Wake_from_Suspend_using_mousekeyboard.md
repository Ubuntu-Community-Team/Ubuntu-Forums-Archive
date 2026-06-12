---
title: "Wake from Suspend using mouse/keyboard"
date: 2011-07-25
forum: General Help
---

### Post by snorlaxsnooz on 2011-07-25
Alright, 
I want my desktop to wake from suspend by either pressing a key on the keyboard, or clicking the mouse.  It is a giant pain to reach into the cabinet where my tower is to push the power button to resume from suspend.  

I had, since 9.10, used the solution in [this thread ]("http://ubuntuforums.org/showthread.php?p=4466270")with great success, and it worked every time.  I am now using 10.04. Recently, an upgrade (i think to the kernel) broke the functionality of that fix, now only the power button will wake from suspend.  Anyone have any idea what to do to get that back? 

Thanks so much for your help!

PS - cat /proc/acpi/wakeup looks like this:

```
Device    S-state      Status   Sysfs node
VBTN      S4    *enabled   
PCI0      S5     disabled  no-bus:pci0000:00
PCI4      S5     disabled  pci:0000:00:1e.0
PCI2      S5     disabled  pci:0000:00:1c.0
PCI3      S5     disabled  
PCI1      S5     disabled  pci:0000:00:01.0
PCI5      S5     disabled  pci:0000:00:1c.4
PCI6      S5     disabled  pci:0000:00:1c.5
USB0      S3     enabled   pci:0000:00:1d.0
USB1      S3     enabled   pci:0000:00:1d.1
USB2      S3     enabled   pci:0000:00:1d.2
USB3      S3     enabled   pci:0000:00:1d.3

```

---

### Post by snorlaxsnooz on 2011-10-16
I also had this set up nicely on 9.10, then for a while on 10.04.  After a kernel update, even with all USBs enabled in /proc/acpi/wake/, you need to use the power button to wake from suspend.  Its sort of a pain for a desktop setup.  Anyone have any clues?

---

### Post by freddybob on 2011-10-23
I'd also like a solution to this for Oneiric 11.10.

---

### Post by rcauston on 2011-10-26
I've got this same problem on a X-less 11.10 server installation. How do I either disable suspend entirely (checked BIOS, cannot turn entirely off either S1 or S3 selectable, MB is a Sapphire IPC-AM3DD785G) or get this darn box to get up and serving SMB when any network queries are directed at it?
 
I get sporadic wake-on lan and most of the time the server just suspends and never wakes up again. Neither my wireless Logitech keyboard nor the power button seem to wake the box thou all lights are on and fans are running. Nothing is shown on screen.
 
This is very frustrating since it's a media server in the cellar that has happily spun the disks up as needed previously. 
 
$ cat /proc/acpi/wakeup
Device S-state Status Sysfs node
PCE2 S4 *disabled pci:0000:00:02.0
PCE3 S4 *disabled
PCE4 S4 *disabled pci:0000:00:04.0
PCE5 S4 *disabled
PCE6 S4 *disabled
PCE7 S4 *disabled
PCE9 S4 *disabled
PCEA S4 *disabled
PCEB S4 *disabled
PCEC S4 *disabled
SBAZ S4 *disabled pci:0000:00:14.2
P0PC S4 *disabled pci:0000:00:14.4
UHC1 S4 *disabled pci:0000:00:12.0
UHC2 S4 *disabled pci:0000:00:12.1
UHC3 S4 *disabled pci:0000:00:12.2
USB4 S4 *disabled pci:0000:00:13.0
UHC5 S4 *disabled pci:0000:00:13.1
UHC6 S4 *disabled pci:0000:00:13.2
UHC7 S4 *disabled pci:0000:00:14.5
PWRB S4 *enabled
 
i've fiddled with ethtool to enable WOL @ startup with 
 
ethtool -s eth0 wol pg
 
and still I get ridiculous startup delays and by judging the uptime after it sometimes actually starts up it seems that the darn thing reboots from scratch when it wakes from standby. (usually down to abt 8min when the server comes up even though last real reboot was days ago). :confused:

---

### Post by jacdaniels on 2012-02-21
i also would like to fix it, but it looks like no one knows how to correct this!

---

### Post by snorlaxsnooz on 2012-06-12
SOLVED!!!!!!

I followed the directions here 

[http://www.linuxquestions.org/questions/linux-general-1/resume-from-suspend-with-a-specific-device-840040/](http://www.linuxquestions.org/questions/linux-general-1/resume-from-suspend-with-a-specific-device-840040/)

In case that post gets deleted, here is the pertinent part:

> Nevertheless that wasn't enough to get it work. I looked in gconf-editor  in apps/gnome-power-manager/general but I have no can-suspend or  something similar... (I'm running on 10.10, with 10.04 I could suspend  only once, afterwards the computer didn't go to suspend, just black  screen then login screen)
So I looked in /sys/ and found that 'cat  /sys/bus/usb/devices/2-1/power/wakeup' (notice the 2.1 as bus 2 device 2  (0,1,...) gave 'disabled' so a 
echo enabled > /sys/bus/usb/devices/2-1/power/wakeup
and now I can wake-up with the remote when I want 

So once i had the devices enabled in both /proc/acpi/wakeup and /sys/bus/usb/devices/X-X/power/wakeup , everything works again!


 that took long enough.

---

