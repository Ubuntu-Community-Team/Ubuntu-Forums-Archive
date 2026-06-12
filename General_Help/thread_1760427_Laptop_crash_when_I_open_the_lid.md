---
title: "Laptop crash when I open the lid"
date: 2011-05-16
forum: General Help
---

### Post by mrpenguin on 2011-05-16
I am running Ubuntu 11.04
I have a Asus Altec Lansing N61JQ-X2 laptop

Sometimes, not all the time, when I close the lid of the laptop and come back later on and open the lid the log in screen wont come up for me to enter my password. I press keys everywhere but nothing will bring up the log in screen, the only thing I can do then is to press the on button till the computer shut down and then restart again.

I had this problem with Ubuntu 10.10 as well but it seems i have this problem more often with 11.04

Any idea why this is happening and how to fix this ?

Thanks

---

### Post by mrpenguin on 2011-05-21
Anybody with an idea ?

---

### Post by linuxinstalledfromhdd on 2011-05-21
run a spec check of your system and post the results here so we can see what you have running.

---

### Post by mrpenguin on 2011-05-21
> **linuxinstalledfromhdd said:**
> run a spec check of your system and post the results here so we can see what you have running.

How do I do that ?

---

### Post by linuxinstalledfromhdd on 2011-05-21
Post as much information about your system that you can so we can find out what the cause might be.

---

### Post by 5149.5 on 2011-05-21
How much ram do you have and how is your swap set up? How do you have power management setup for action to take when you close the lid?

---

### Post by mrpenguin on 2011-05-21
This is from the website I bought the computer from ..... no windows 7 though as I run Ubuntu 11.04

ASUS N61JQ-X2 16" Laptop
  Memory Type: 	DDR3
	

  Memory Speed: 	PC3-8500
	

  Memory Speed MHz: 	1066MHz
	

  Memory Slots (Total): 	2
	

  Total Memory Size: 	4GB
	

  Maximum Memory Supported: 	8GB
	

  Display Type: 	LED backlight
	

  Screen Size: 	16"
	

  Maximum Resolution: 	1366 x 768
	

  Capacity: 	320GB
	

  Drive Types: 	Hard Drive
	

  Hard Drive Speed: 	5400 RPM
	

  Processor Brand: 	Intel
	

  Processor Class: 	Core i7
	

  Processor Type: 	Quad-Core
	

  Processor Speed: 	1.60GHz
	

  Processor Number: 	i7-720QM
	

  Graphics Description: 	Dedicated Graphics
	

  GPU/VPU: 	ATI Mobility Radeon HD 5730
	

  Video Memory: 	1GB DDR3
	

  Lifestyle: 	Entertainment
	

  Condition: 	New
	

  Operating Systems: 	Windows 7 Home Premium 64-Bit
	

  Operating System Licenses Included: 	Windows 7 Home Premium 64-Bit
	

  Platform: 	Laptop
	

  Expansion Ports: 	1 - Express Card Slot
	

  Optical Drive: 	DVD Super Multi Burner
	

  Capacity: 	8-in-1
	

  Supplemental Drive Type: 	Media Reader
	

  Media Types: 	Memory Stick
 	Memory Stick Duo
 	Memory Stick PRO Duo
 	Memory Stick PRO
 	Multi Media Card
 	Mini-Secure Digital
 	Secure Digital
 	 xD-Picture Card
	

  Audio Description: 	Integrated Audio
	

  Audio Chipset: 	SRS Premium Sound
	

  Audio Channels: 	Altec Lansing speakers
	

  Integrated Microphone: 	Yes
	

  PS/2 Mouse Connectors: 	N/A
	

  PS/2 Keyboard Connectors: 	N/A
	

  Serial Communication Ports: 	N/A
	

  Parallel Ports: 	N/A
	

  USB Ports (Total): 	2 - USB 2.0
 	1 - USB 3.0
	

  FireWire Ports: 	N/A
	

  Fast Infrared Ports (FIR): 	N/A
	

  LAN Ports: 	1
	

  Modem Ports: 	N/A
	

  Audio Out Jacks: 	1 - Audio Out/SPDIF Shared
	

  Line In Jacks: 	N/A
	

  Microphone Jacks: 	1
	

  VGA Ports: 	1
	

  DVI Video: 	N/A
	

  HDMI Ports: 	1
	

  S-Video Connectors: 	N/A
	

  Port Replicator/Connector: 	N/A
	

  eSATA Ports: 	1
	

  Communications Description: 	Integrated LAN
 	Integrated Wireless LAN
	

  Interface Type: 	RJ-45 Ethernet Connector
 	802.11b/g/n Wireless Networking
	

  Data Transfer Rate: 	10/100/1000Mbps Network
 	Up to 300 Mbps
	

  Protocols: 	802.11b
 	802.11g
 	802.11n
	

  Width: 	15.4"
	

  Height: 	1.2" - 1.5"
	

  Depth: 	10.6"
	

  Weight: 	6.5 lbs
	

  Mouse Type: 	Touch Pad
	

  Keyboard Type: 	Fullsize with Numberpad
	

  Battery Type: 	6-Cell Lithium-ion
	

  Color: 	Brown
	

  Specification Notes: 	[6] To provide the most accurate specifications, the specifications listed are base upon information provided by the vendor.
	

  Integrated Webcam: 	Yes
	

  Webcam Resolution: 	2.0MP

---

### Post by mrpenguin on 2011-05-21
When laptop lid is closed it is set to Suspend

---

### Post by 5149.5 on 2011-05-21
> **mrpenguin said:**
> When laptop lid is closed it is set to Suspend

I think that would be a suspend to ram and you should be OK. There is an old [bug]("http://goo.gl/kivGl") against N61s for not suspending on 10.10. I didn't see any resolution to it.

---

### Post by mrpenguin on 2011-05-27
Why would this be a bug with the laptop itself and not ubuntu ?
When I open the lid nothing works at all ... pressing keys on my keyboard dont wake up the computer.
Its as if the entire computer crash when I close the lid

---

### Post by mrpenguin on 2011-05-27
I forgot to mention that this also happened with Ubuntu 10.10 running on an HP laptop, the Asus is a new laptop and is running Ubuntu 11.04, this is happening 10x more on the new laptop with 11.04

On the HP laptop with 10.10 it happened about 3x a week ... with the Asus with 11.04 it happens every time I close the lid.

---

### Post by ThatCoolGuy220 on 2011-05-27
Open: Synaptic Package Manager:

Install Following packages:

- lm-sensors

- libsensors3

- libsensors4

- fancontrol

- cpufreqd

Restart and it should be working.

I discovered this trying to fix my fans also noticed it fixed the closed lid bug.

---

### Post by ThatCoolGuy220 on 2011-05-28
IF worked Mark this thread as solved so other ppl coul find it faster.

---

### Post by mrpenguin on 2011-05-28
That did not work at all
I insltalled everything above, restarted my computer and closed the lid then opened the lid andthe log in screen did not come up

---

### Post by ThatCoolGuy220 on 2011-05-29
Im sorry for not giving you a correct answer

---

### Post by mrpenguin on 2011-05-30
> **ThatCoolGuy220 said:**
> Im sorry for not giving you a correct answer

Its got to be Ubuntu because I had the same problem on another laptop.
today I didn't close the lid and after 2 hours the log in screen did not come on when I tried to wake the computer.

---

### Post by JCM_Pico on 2011-05-30
The computer is probably suspending when you close de lid, and that is causing some trouble... I had the same problem once.
When reading the thread I could understand if you have deselected  the option for the pc suspend when you close the lid....

---

