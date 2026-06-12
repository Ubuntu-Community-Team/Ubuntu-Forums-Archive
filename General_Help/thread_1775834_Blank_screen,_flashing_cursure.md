---
title: "Blank screen, flashing cursure?"
date: 2011-06-05
forum: General Help
---

### Post by Bobrm2 on 2011-06-05
I've a blank screen, with a flashing cursure, since yesterday afternoon. I thing the message, after control/alt/delete is:

   Checking NVAH, but it moves so quickly that I'm not for sure what the message says, let alone what it means.

  I am building a new box from scratch. I've a memory stick with Ubuntu 10.10 ISO and made through "Startup Disk" creator.

  Gparted ran, and I think this is where the problem is. I formatted the HDD with ./ 12 gigs, /boot 5 gigs, /data 38 gigs, ./swap with 12 gigs.

   Can someone tell me what happening, how to stop the screen so that I make out what the "checking ????" is saying. Or, how can I get back to square one? Ctrl/alt/delete does a restart essentially. Turning off the box and back on gets a very brief glance at the BIOS splash screen and the the blinking curser.

thank Bob R, who now is going outside to see if he can reinstall the deck on the riding mower.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
what hardware is in it?

---

### Post by Bobrm2 on 2011-06-05
This should cover the Hard ware? Thanks for the quick response

Items Ordered
ECS IC780M-A Motherboard - AMD 770, Socket AM2+, ATX, DDR2, Dual Channel, PCIe, RAID (S458-1342)	1	$49.91	$49.91
 	
AMD Phenom X4 9750 Quad Core Processor - 2.40GHz, 4MB Cache, 3600 MT/s FSB, Quad-Core, Socket AM2+, OEM Processor (A79-9751)	1	$52.30	$52.30
 	
Patriot PSD22G80026 2048MB PC6400 DDR2 Memory - 800MHz, 1x2048MB, Non-ECC, Unbuffered (P33-6096)	1	$27.38	$27.38
 	
Seagate ST3500418AS Barracuda 7200.12 Hard Drive - 3.5", 7200 RPM, SATA 3G, 500GB, 16MB Cache (OEM) (TSD-500AS7)	1	$38.84	$38.84
 	
DiabloTek CPA-0280 Elite ATX Mid Tower Case - ATX, Micro ATX, 450W PSU, 2x Ext 5.25", 1x Ext 3.5", 2x Int 3.5", 2x USB 2.0 Front Ports, Black (D15-3003)	1	$33.45	$33.45
 	
Cooler Master Hyper N520 CPU Cooler - Socket LGA 775, AM2, AM2+, 1156, AM3, 1366 (C283-1202)	1	$29.99	$29.99
 	
EVGA 01G-P3-1235-LR GeForce GT 240 Video Card - 1024MB DDR3, PCI-Express 2.0, DVI, HDMI, VGA (E145-0248)	1	$69.99	$69.99
 	

Sabrent 802.11n Wireless PCI Controller Card - 802.11n/g/b, 300Mbps, 40/64/128-bit WEP encryption (M501-4020)

Lite-On IHAS424-98 Internal DVD Writer - DVD+R 24X, DVD-R 24X, DVD+RW 8X, DVD-RW 6X, Lightscribe (L12-1350)	1	$29.99	$29.99
 	
Logitech LS21 2.1 Stereo Speakers - 2.1 Channels, 7-Watts RMS, 2" High-excursion Metallic Drivers, 4" 4-Watts RMS Max-X High-excursion Subwoofer (L23-8622)	1	$24.99	$24.99
 	
Acer S211HL bd 22" Class LED Monitor - 1080p, 1920x1080, 12000000:1 Dynamic, 5ms, VGA, DVI (A179-2150)	1	$129.99	$129.99
 	
Ultra ULT40136 Silent 80mm Case Fan - Dual Ball Bearing, Silent, 1800 RPM, 23.15 CFM, 20.4 dBA (ULT40136)

---

### Post by pqwoerituytrueiwoq on 2011-06-05
are you able to boot to recovery mode?
it is likely a driver issue with the nvidia card
which version of ubuntu are you using
i would try installing nvidia-current, nvidia-settings
[FONT=Courier New]sudo apt-get install nvidia-current nvidia-settings[/FONT]

if it fails i would get it from nvidia's site directly
```
sudo service gdm stop
sudo mkdir /opt/nvidia
cd /opt/nvidia
sudo wget http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.19/NVIDIA-Linux-x86_64-270.41.19.run
sudo chmod +x ./NVIDIA-Linux-x86_64-270.41.19.run
sudo ./NVIDIA-Linux-x86_64-270.41.19.run
```
with this method you will have to reinstall the driver after every kernel update

---

### Post by Bobrm2 on 2011-06-05
Can't get to a terminal??  also, disk is formated, but no system in place.  Just finished the Gparted and was attempting to download Ubuntu 10.10. No splash screen, well BIOS flashes but I don't know which key to select recovery mode??? Thanks

---

### Post by pqwoerituytrueiwoq on 2011-06-05
so you never got it installed (there is no recovery mode then)
i assume the cd/usb would not boot then
you may want to use the alternate cd to bypass the driver issue for the install
then boot to recovery mode and install the driver you need then 
[FONT=Courier New]sudo service gdm start[/FONT]
you may have better luck with 10.04.2

---

### Post by Bobrm2 on 2011-06-05
By alternate CD do you mean the memory stick? As I said I tried to use Startup disk creator to load the system. 

 Can I go back to CMOS on the mother board and switch the jumper to pins 2 and 3 for ten seconds plus the back to pins 1 and 2 to reset the system? 

Bob R

---

### Post by Bobrm2 on 2011-06-05
Tried the memory stick after a reboot got the BIOS screen briefly, then it's searching for ???? To quick for my eyes to read the checking....

---

### Post by pqwoerituytrueiwoq on 2011-06-05
by alt cd i mean this
[http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-amd64.iso.torrent)

[http://releases.ubuntu.com/lucid/ubuntu-10.04.2-alternate-amd64.iso.torrent](http://releases.ubuntu.com/lucid/ubuntu-10.04.2-alternate-amd64.iso.torrent)

the look of the bootable cd is more like a xp install disk

---

### Post by Bobrm2 on 2011-06-05
downloaded the torrent inserted cd into new box, with the same results?

Do I make a startup disk of the ISO.

---

### Post by Bobrm2 on 2011-06-05
Before this problem began, I had 11.04 and 10.10 functional off the memory stick. I inserted GParted and partitioned the HDD as I said above. Is the problem somehow related to the partition table, and how do I change that? Seems like that's where to began, but I sure don't know.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
open gparted
if you want to wipe the hdd
device -> create new partition table
other wise click the partitions you do not want and click delete (looks like [this]("http://cdn3.iconfinder.com/data/icons/musthave/128/Cancel.png"))

---

### Post by Bobrm2 on 2011-06-05
No indication that Gparted was seen, but I set BIOS to load from DVD first, HDD 2nd.

---

### Post by Bobrm2 on 2011-06-05
The message "Searching n???" it doesn't say searching for, it's like the program(?) is seeking something on the HDD, but not like something is unplug? If I could slow the BIOS screen down so I could see what it is searching for.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
is the hdd making a clicking sound (wondering if it is faulty)
check the smart status
system -> administration -> disk utility

---

### Post by Bobrm2 on 2011-06-05
Have tried "ESC" to get into "Hidden" GRUB, with no luck?

---

### Post by Bobrm2 on 2011-06-05
nothing to indicate there's a problem with the HDD.

---

### Post by Bobrm2 on 2011-06-05
Nothing possible unable to check "Disk Utility" or smart status.

---

### Post by Bobrm2 on 2011-06-05
Does this make any sense:

[http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29](http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29)

---

### Post by jim_deadlock on 2011-06-05
Bob, [this chap had exactly the same problem yesterday]("http://ubuntuforums.org/showthread.php?p=10902341"), you have some kind of hardware issue and you may be able to fix it simply by moving your hardware around to other slots/connectors on your motherboard.

---

### Post by jim_deadlock on 2011-06-05
By the way, the "black screen" issue is not the same as "black screen with flashing cursor".

---

### Post by Bobrm2 on 2011-06-05
The checking message is: Checking NVRAM. So I'm assuming it is checking some kind of 'Ram Memory" I changed the location of the ram on the motherboard. ECS say if you have only one stick of ram it should be in the third slot (1 thru 4). Still no luck, and I better make sure that I understand which is the third slot, or I'll have two problems.

---

