---
title: "Issues with Suspend, Hibernate, and Shut Down in 11.04"
date: 2011-05-28
forum: General Help
---

### Post by anonymousdude on 2011-05-28
I'm having some major problems with suspend, hibernate, and shutting down.

When I put my computer into suspend or hibernate, my screen goes blank/black but judging from the sound coming from my computer it does not sound like it is actually going into suspend/hibernate.  The real problem though is no matter what I do, I can't get the blank/black screen to go away.  I tried numerous keys, mouse clicks, pressing the power button once.  Nothing works and eventually I have to hold the power button down until the system powers off.

The shutting down issue is probably not as severe but I'm posting it because it's most likely related.  When I chose Shut Down, everything on the desktop disappears but my wallpaper image remains, and the system never powers off.  Pressing the power button once doesn't work either and I have to hold it down until it powers off.

Not sure if it's a hardware issue, but my system specs can be found here..

[http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=BV533AA%23ABA]("http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=BV533AA%23ABA")

Any suggestions would be greatly appreciated!

---

### Post by lmn. on 2011-05-28
yerp, more than likely an install or hardware issue. 

if it only started happening recently it's bound to be install-related and will probably be fixed after a reinstall/ recovery -fix broken packages

---

### Post by anonymousdude on 2011-05-28
> **lmn. said:**
> yerp, more than likely an install or hardware issue. 

if it only started happening recently it's bound to be install-related and will probably be fixed after a reinstall/ recovery -fix broken packages

Well it's a new machine so this is the first version of Ubuntu I've ran/installed on it.  Is there any steps I can take besides re-installing?

---

### Post by wildmanne39 on 2011-05-28
> **anonymousdude said:**
> I'm having some major problems with suspend, hibernate, and shutting down.

When I put my computer into suspend or hibernate, my screen goes blank/black but judging from the sound coming from my computer it does not sound like it is actually going into suspend/hibernate.  The real problem though is no matter what I do, I can't get the blank/black screen to go away.  I tried numerous keys, mouse clicks, pressing the power button once.  Nothing works and eventually I have to hold the power button down until the system powers off.

The shutting down issue is probably not as severe but I'm posting it because it's most likely related.  When I chose Shut Down, everything on the desktop disappears but my wallpaper image remains, and the system never powers off.  Pressing the power button once doesn't work either and I have to hold it down until it powers off.

Not sure if it's a hardware issue, but my system specs can be found here..

[http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=BV533AA%23ABA]("http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=BV533AA%23ABA")

Any suggestions would be greatly appreciated!

Hi, it is probably your video card, I would disabled sleep hibernation that does not work on my system either. You can go to administration log file viewer and look through all the logs and see if you see any error messages.

---

### Post by wildmanne39 on 2011-05-28
> **anonymousdude said:**
> I'm having some major problems with suspend, hibernate, and shutting down.

When I put my computer into suspend or hibernate, my screen goes blank/black but judging from the sound coming from my computer it does not sound like it is actually going into suspend/hibernate.  The real problem though is no matter what I do, I can't get the blank/black screen to go away.  I tried numerous keys, mouse clicks, pressing the power button once.  Nothing works and eventually I have to hold the power button down until the system powers off.

The shutting down issue is probably not as severe but I'm posting it because it's most likely related.  When I chose Shut Down, everything on the desktop disappears but my wallpaper image remains, and the system never powers off.  Pressing the power button once doesn't work either and I have to hold it down until it powers off.

Not sure if it's a hardware issue, but my system specs can be found here..

[http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=BV533AA%23ABA]("http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=BV533AA%23ABA")

Any suggestions would be greatly appreciated!
Hi, I also read a post that some wireless cards are causing the same problems that you are having, but I did not see a solution.

---

### Post by katykat on 2011-05-29
I memory serves me right this may also be an issue with the size of the swap partition. Google for 'ubuntu hibernate problems' - something should come up about swap partitions, especially when disk space is running low. You will also need to delete the old hibernate file...

Its also a good idea to disable all unneeded daemons, especially on new verisons such as Natty, where all the bugs are not likely to be ironed out.

---

### Post by anonymousdude on 2011-05-29
> **wildmanne39 said:**
> Hi, it is probably your video card, I would disabled sleep hibernation that does not work on my system either. You can go to administration log file viewer and look through all the logs and see if you see any error messages.

Thanks for the info.  I disabled hibernation for the time being.  Of course I'm still having the problem at shutdown though where I have to force a shutdown.

I'm king of a Linux noob.  How can I check which driver I'm using for my video card?  I was told it could be an issue of needing to switch to a proprietary version of the driver if one is available and I'm not currently using it.

---

### Post by anonymousdude on 2011-05-29
> **katykat said:**
> I memory serves me right this may also be an issue with the size of the swap partition. Google for 'ubuntu hibernate problems' - something should come up about swap partitions, especially when disk space is running low. You will also need to delete the old hibernate file...

Its also a good idea to disable all unneeded daemons, especially on new verisons such as Natty, where all the bugs are not likely to be ironed out.

When I issue the free command it shows that my memory is 5855348 and my swap is 5953232.  So my swap should be good right?

---

### Post by anonymousdude on 2011-05-29
Not sure if this info is helpful, but below is the output of lshw for my graphics card and network cards.  I also attached a pdf of the full lshw output.


id:	
display
description:	VGA compatible controller
product:	Core Processor Integrated Graphics Controller
vendor:	Intel Corporation
physical id:	
2
bus info:	
pci@0000:00:02.0
version:	18
width:	64 bits
clock:	33MHz
capabilities:	msi pm vga_controller bus_master cap_list rom
configuration:	
driver	=	i915
latency	=	0
resources:	
irq	:	42
memory	:	fb800000-fbbfffff
memory	:	d0000000-dfffffff
ioport	:	cc00(size=8)



id:	
network
description:	Wireless interface
product:	RT3090 Wireless 802.11n 1T/1R PCIe
vendor:	Ralink corp.
physical id:	
0
bus info:	
pci@0000:03:00.0
logical name:	
wlan0
version:	00
serial:	1c:65:9d:d1:61:31
width:	32 bits
clock:	33MHz
capabilities:	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	rt2800pci
driverversion	=	2.6.38-8-generic-pae
firmware	=	0.11
latency	=	0
link	=	no
multicast	=	yes
wireless	=	IEEE 802.11bgn
resources:	
irq	:	17
memory	:	fbff0000-fbffffff

---

### Post by anonymousdude on 2011-05-30
I figured out that it's my wireless adapter.  Fortunately, this is my desktop and I'm hardwired to my router so I just disabled it with no consequence and it works now.

The only issue I'm having now is that when I take it out of hibernate it loads grub instead of just going straight back to Ubuntu.  Anyone know a way to fix that?

---

