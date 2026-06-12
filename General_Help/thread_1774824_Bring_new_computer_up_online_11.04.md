---
title: "Bring new computer up online 11.04"
date: 2011-06-03
forum: General Help
---

### Post by Bobrm2 on 2011-06-03
Well, I got in it this time. Bought the components and have them installed.. Turned on the box, several beeps, and then American Mega trends screen came up. Move into BIOS to look around but left everything as "Default". The F header is connected, DVD lights up, power off and on, all fans are also running. The cooler fan, two additional case fans, and the fan on the GForce video card are also running.

  So, burned an ISO of 11.04, and as the screen placed it in DVD drive, hit a key and got a request to "Insert Boot Media.......and hit a key, and hit a key,,... Can't get passed the request.

  I don't know whether to try to format the HD with "Partition Magic". or what. Is there a "HowTo' out there, or could someone give me a hand. Thanks in advanced. I have an ISO of PM also.

Components are:
ECS IC780M-A Motherboard - AMD 770, Socket AM2+, ATX, DDR2, Dual Channel, PCIe, RAID (S458-1342)	1
 	
AMD Phenom X4 9750 Quad Core Processor - 2.40GHz, 4MB Cache, 3600 MT/s FSB, Quad-Core, Socket AM2+, OEM Processor (A79-9751)	
 	
Patriot PSD22G80026 2048MB PC6400 DDR2 Memory - 800MHz, 1x2048MB, Non-ECC, Unbuffered (P33-6096)	1
 	
Seagate ST3500418AS Barracuda 7200.12 Hard Drive - 3.5", 7200 RPM, SATA 3G, 500GB, 16MB Cache (OEM) (TSD-500AS7)	1
 	
DiabloTek CPA-0280 Elite ATX Mid Tower Case - ATX, Micro ATX, 450W PSU, 2x Ext 5.25", 1x Ext 3.5", 2x Int 3.5", 2x USB 2.0 Front Ports, Black (D15-3003)
 	
Cooler Master Hyper N520 CPU Cooler - Socket LGA 775, AM2, AM2+, 1156, AM3, 1366 (C283-1202)
 	
EVGA 01G-P3-1235-LR GeForce GT 240 Video Card - 1024MB DDR3, PCI-Express 2.0, DVI, HDMI, VGA (E145-0248)	

18:29 hrs.

Following not detected: SATA 1 thru 4, IDE Master and Slave. Connection made on HD. Perhaps the Cable isn't connected to the power supply?



		

Bob R

---

### Post by wolfen69 on 2011-06-03
Partitioning the hard drive has nothing to do with your problem. Partitioning can be done once the install process has begun. You need to check your BIOS settings for boot device order and such.

Also, did you check the integrity of the burned disc?

---

### Post by linuxinstalledfromhdd on 2011-06-03
Boot order BIOS settings.

Make sure you buses are in the right sequence on the mb. 

Check your jumpers.

---

### Post by Bobrm2 on 2011-06-03
I think you guy have solved the problem 1st boot device is the "HD". So, now I'll move that to second and the DVD is 1st. Have to figure how to change 1st to 2nd etc. and by the way Enhanced Halt is "Disabled"? and Boot other Device is "Yes" What other device? Is yes correct.  I checked the jumpers. As per factory, and only one I've moved is the CMOS.

Don't understand "Bus on the motherboard"

---

### Post by Bobrm2 on 2011-06-03
I let the burned run a check sum, but I am not positive about the ISO.  Switched the HD to the second position and the DVD to first, restart saw no change, still requesting me to insert boot media?

---

### Post by linuxinstalledfromhdd on 2011-06-03
Install it from a USB Flash Drive instead. Just bypass this issue until you can at least have something to work with.

---

### Post by Bobrm2 on 2011-06-03
Well, that's different, msg. says "Missing operating system_" With a flashing courser. Is the ISO being uploaded now?

---

### Post by wolfen69 on 2011-06-03
Usually you can hit F12 and choose boot device. Try that.

---

### Post by Bobrm2 on 2011-06-03
Going to have to start using my head. created a startup disk via the flash drive. Looks like we have an operating system. Yes, 11.04 is waiting for me. Thanks a lot to both of you 


Bob R

---

### Post by linuxinstalledfromhdd on 2011-06-03
Here is a nice walk-through after you get it updated as well:

 [http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by Bobrm2 on 2011-06-03
Thank you, just looked up and I don't have a large enough HD, to install 11.04. That's strange because I've got it it's own partition on an older computer. Somethings haywire, the new HD is 500 gigs. Plenty of room. I really don't understand that. It's a SATA drive. only power and data hookup. I didn't even see a master/slave header? Anyway, I've an ISO for 10.10 for now.  

Thanks for all the help. I'll mark this one solved, for now.

Bob R

---

