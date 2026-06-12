---
title: "stable on livecd, crashes after installation"
date: 2011-05-22
forum: General Help
---

### Post by aaronsilber on 2011-05-22
I can boot off of the Natty LiveCD, run it for days fine. Install, everything's smooth. Boot up and run some updates. That's where it hung the first time around. Display froze, cursor and keyboard would not respond, audio was stuck looping. This was a pain because it corrupted some stuff with apt. Whatever, a one-time occurrence, right? Nope.

Any point from power-on onward is "eligible" for a crash. It seems to be random, but there also seems to be a trend of it crashing earlier on as time proceeds. This is a custom built computer, and I've tried other Linux distros like Debian and 9.04 UNR, they all crash somewhere in the install. Leaves me thinking it's a hardware fault, but why would it run perfectly fine off of CD but die when installed then?

All help is greatly appreciated. Thanks in advance!

Specs:
[LIST]
[*]AMD Athlon II X4 645 Propus 3.1GHz
[*]MSI 870-G45 AM3 AMD 770 ATX AMD Motherboard
[*]Seagate Barracuda ST31000524AS 1TB
[*]G.SKILL Ripjaws Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1066 (PC3 8500)
[*]LG Black Blu-ray Drive SATA Model UH12LS28 OEM LightScribe Support
[*]Diablotek PHD Series PHD550 550W ATX12V V2.2 Power Supply
[*]ASUS EAH5670/DI/1GD5 Radeon HD 5670 (Redwood) 1GB 128-bit GDDR5 PCI Express 2.1 x16 HDCP Ready CrossFireX Support Video Card

[/LIST]

---

### Post by linuxinstalledfromhdd on 2011-05-22
If you have any doubt about the quality of worksmanship on a custom unit, i.e. you didn't build it yourself, or can contact the person that did for support, what I would try first is..

See if the MB has on-board video.  If it does, use it. 

Remove the video card you have in it now. 

Do an install, and see if the problem redevelops again. 

Try that for each piece of potentially faulty hardware.  

I know, it is very time consuming, but it is one way to be totally certain what the problem is when it comes to troubleshooting hardware.

---

### Post by ericzmeh on 2011-05-22
If Ubuntu is running fine on the LiveCD but crashes during/after install to your HDD, then I would assume the problem lies with the HDD.  I had this same problem with a HDD i just replaced, as it was spinning down to 0 rpm while the OS was running, causing the computer to freeze.  Grab a copy of Hiren or go to SeaGate's website and download a diagnostics utility to run from a boot CD or other bootable device, and do a full media scan on the drive.  This will potentially let you know if you are having HDD problems, as their software is capable of also detecting most physical drive faults.

---

### Post by aaronsilber on 2011-05-23
Alright, I'm going to try some disk diagnostics once I get back to the machine. Good idea.

Also, it doesn't have onboard video, sadly... I will try another video card in it as well.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Okay good.  Let us know what you find out so we can try to help you out.

---

### Post by aaronsilber on 2011-05-30
Windows installation would also crash at a certain stage in the installer.

Ran Seagate DiskUtils for DOS on all 3 drives, all checked out. Beefed up the power supply, same crashes. Took out one of two of the 4gb sticks of memory and it began to operate fine.

Currently running off the remaining 4gb and it works great.

---

