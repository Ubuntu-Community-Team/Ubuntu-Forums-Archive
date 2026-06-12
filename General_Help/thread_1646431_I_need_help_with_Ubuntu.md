---
title: "I need help with Ubuntu"
date: 2010-12-15
forum: General Help
---

### Post by izz.y on 2010-12-15
[CENTER]_**[SIZE="2"]Overview[/SIZE]**_[/CENTER]
Hello Fellow Forum Members,
I am fairly comfortable with Ubuntu, I have been using it for a few years now, and I have done all sorts of things like compiling kernels, and installing software from source code. I am not sure how to simply explain my dilemma/what I am trying to do, so here is a breakdown:

[CENTER]_**[SIZE="2"]My Computer[/SIZE]**_[/CENTER]
In my computer, I have an ASUS M4A78L-M motherboard which has the problematic "AMD SB710" south bridge. I have an AMD Athlon II X3 440 processor, and I unlocked it to a Phenom II X4 B40, and over clocked it to 3.55 GHZ, and it is fully stable (Best $75 bucks I've spent). I have 3 hard drives, one is a Sata drive made by a company called excelstor technologies and is 250GB (Here is the OEMs data sheet: [http://www.excelstor.com/uploadfile/CN11877%20D10390%20Rev1.0%20J9250%20Datasheet%20EN.pdf](http://www.excelstor.com/uploadfile/CN11877%20D10390%20Rev1.0%20J9250%20Datasheet%20EN.pdf)), I have XP and 7-64bit installed with the windows boot loader on that. I have a 120GB Toshiba IDE hard drive from a laptop, and an IDE to SATA converter, and it is mounted with brackets internally, and this is only used for storage. Lastly, I have a 1 TB Seagate drive that I use for Ubuntu 10.04 64-bit, this is my default boot device, and I am using GRUB (not GRUB 2). I also have an Nvidia 9800GT, and 4GB of DDR2-5300 (I chose slow good RAM thats slow, so I can over clock my processor higher). I also have 2 old IDE CD/DVD drives/Burners.

[CENTER]_**[SIZE="2"]My Relationship With Ubuntu[/SIZE]**_[/CENTER]
Ubuntu boots and runs fine off a USB Flash Drive, Memory Card, or CD/DVD, but I had a lot of hassle getting it to install. I was never able to boot outside of recovery mode, and when I would start recovery mode, and about 80% of the time I would get a SATA link failure (I thought it was the cheap IDE to SATA adapter, but I disconnected that, and it makes no difference), and my computer would stop booting at that. I looked around the forums, and this is a bug in Linux with my south bridge, and I had to build a new kernel to run it. I built my own X86-64 2.6.35.9 kernel with some tweaks (like SATA_PMP_Multiplier = N, this was one on many forums), and I couldn't boot it, and I realized I forgot to make the Initrd. I made that, and booted the kernel, but I got a different SATA error, so I researched that and fixed the problem with some GRUB command line work. My computer will now load up Ubuntu from Recovery Mode and my kernel about 60% of the time, and the remaining 40% of the time, I would get some weird SATA errors (Usually including the words "softreset failed"), but I have had 0% success rate booting Ubuntu otherwise. When I boot into recovery mode, I just have to login as root, and then start GDM manually (/etc/init.d/gdm start works 95% of the time), and I could then fully use Ubuntu problem free. 


[CENTER]_**[SIZE="2"]My Ordeal[/SIZE]**_[/CENTER]
I am very tolerant of my hassles with Ubuntu, and I can tolerate the text, the slow boot up times, and the fact that I have to restart up to 10 times sometimes just to get Ubuntu to boot. It would be nice if I could get rid of these, but my main pet-peeve is logging on as root, and starting GDM manually. I would like to know how to create some sort of boot entry, or someway that Ubuntu starts how it usually would under recovery mode, and then it will automatically login as root, and start GDM (Probably through some script), this way I can just keep on restarting until it boots.

[CENTER]_**[SIZE="2"]Additional Notes[/SIZE]**_[/CENTER]
My Motherboard has 3 SATA modes, AHCI, IDE, and RAID. Ubuntu boots 100% of the time when I set it to RAID, but my motherboard takes a long time to post. AHCI has slightly higher success rate then IDE, but it can't boot Windows then.

I have tried using just the Seagate drive, and disconnecting the other 2, but that does not make a difference.

---

### Post by inso_741 on 2010-12-15
If AHCI works maybe you can try installing AHCI drivers for windows....you can integrate them into the windows installation media using nlite(there are alot of tutorials)

---

### Post by izz.y on 2010-12-15
Thanks for the quick response, AHCI does not always work, it is just trivially more successful. I don't want to reconfigure my bios every time just to boot windows, so I decided to stick with IDE. mode. My main issue is starting GDM though. I also don't feel like reinstalling Windows XP and 7, and slipstreaming drivers.

---

