---
title: "Bug:  ndiswrapper prevents mounting of new USB device types"
date: 2010-08-24
forum: General Help
---

### Post by cypeng on 2010-08-24
Hi all,

I recently noticed a bug with ndiswrapper in Ubuntu 10.4 which would prevent the mounting of new USB device classes.  This bug has been noticed somewhere else, in particular in at least one older Ubuntu version, but has been carried over.  This doesn't seem to be widely discussed, or the solution worked anecdotally, but the problem is actually more general in nature.  At the moment I found a workaround that always works, but I don't have a permanent fix.  

The problem kicks in only after ndiswrapper module is loaded into the kernel.  Devices of the same USB *types* that were recognized *before* ndiswrapper is loaded will continue to work.  For example, an USB memory stick will be mounted fine  if an USB hard disk had already been used at some point before ndiswrapper was loaded.  However, if one plugs in any other new type of device, for example, an USB mouse, after ndiswrapper is loaded, the new USB device will not be mounted.  

The workaround solution is to disable ndiswrapper before introducing a new type of USB device by doing:

      sudo modprobe -r ndiswrapper

Then, plug in the USB device.  After it is successfully mounted, do:

     sudo modprobe ndiswrapper

The corollary is that if ndiswrapper is loaded into the kernel upon boot-up, only USB devices which were present at the boot stage will be recognized.  But performing the above kludge will allow new devices to be recognized.

It'd be nice if someone can come up with a more elegant fix.

Best wishes.

---

### Post by SisterNotes on 2010-08-30
cypeng, thank you for pointing me to your thread. I've got a bug report over in launchpad and will add this link. You've got the best description of the problem. My own work-around is to unplug my wireless usb (which uses ndiswrapper) before booting. Then I can plug in my flash drive or mp3 player followed by the wireless connection. Invariably, I forget and it takes a reboot (meaning shutdown followed by boot-up, because restart will not correct the problem) to sort everything out again.

This is the link to the bug report: 
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/589461]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/589461")

---

### Post by david-emm on 2010-10-24
Thanks cypeng for the work around. I recently dropped my laptop and broke the RJ45 connector - hence the only way I can now use this machine is to use wireless. It's an ACER Travelmate 2200 which uses NDIS and the wireless driver that comes with Windows XP. (It's branded[FONT=Arial][SIZE=1] Linksys [AirConn] INPROCOMM IPN 2220)[/SIZE][/FONT][SIZE=1][FONT=Arial].[/FONT][/SIZE] Only then I found out that I could not reliably access my USB sticks and digital camera. Maybe not a big problem but annoying.
At least now I can get access to these devices when I want.

---

### Post by david-emm on 2011-01-26
I'm running meerkat on an Acer 2201 using ndiswrapper and the windows  neti2220 driver so also was having the same problem as described above.  Then for other reasons I installed Virtual Box 4.0.2 and its addition  for USB 2.0.
Lo and behold on rebooting and without opening up Virtual Box I can now  see my wifi network AND all my USB ports. No problem in mounting or  safely removing and of my USB flash disks. Seems that the Virtual Box  addition has corrected the problem.

---

