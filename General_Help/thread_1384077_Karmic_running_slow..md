---
title: "Karmic running slow."
date: 2010-01-18
forum: General Help
---

### Post by fidelandche on 2010-01-18
Hi went over to Karmic when it first came out and was very happy with the improvments, but just recently my laptop has started to slow down, the boot up speed has decreased by another 40 seconds, it now takes about 90 seconds to boot, the latest version of FF is slow to load pages and at times it can stick. I have installed Chrome which is a lot faster than FF and not noticed any problems yet. I do not have compiz installed, so that is not an issue. I keep away from any dodgy sites, my email is checked on line by antivirus software before I read it, so no virus. I just use it for web browsing, emails, the very odd film and the occassional game which came installed.
 
  So if I remove programs installed under the software centre, will that improve speed? Or is there something else I can do to improve speed?
 
  My specs are [SIZE=1]Processor[/SIZE][SIZE=1]Intel® Celeron® M Processor 440 
1 MB L2 cache | 1.86 GHz | 533 MHz FSB) [/SIZE][SIZE=1]Chipset[/SIZE][SIZE=1]Intel® 943GML chipset [/SIZE][SIZE=1]Display panel[/SIZE][SIZE=1]15.4-inch WXGA (1280 × 800) [/SIZE][SIZE=1]Memory[/SIZE][SIZE=1]Installed memory: 512 MB (2 × 256) 
Total slots: 2 DDR2 slots | Available slots: 0 DDR2 slots
Maximum memory: 2 GB [/SIZE][SIZE=1]Video controller[/SIZE][SIZE=1]Intel® Graphics Media Accelerator 950 
Up to 64 MB of shared video memory [/SIZE][SIZE=1]Audio[/SIZE][SIZE=1]High definition audio - 2 channel [/SIZE][SIZE=1]Hard drive[/SIZE][SIZE=1]80 GB 5400 RPM SATA hard drive [/SIZE][SIZE=1]Optical drive[/SIZE][SIZE=1]8X Multi-format dual layer DVDRW [/SIZE][SIZE=1]Modem[/SIZE][SIZE=1]Integrated V.92 56K modem[/SIZE][SIZE=1]Network[/SIZE]
[LIST]
[*][SIZE=1]10/100 Ethernet [/SIZE]
[*][SIZE=1]Intel® PRO wireless 4965 802.11a/b/g[/SIZE]
[/LIST]
 
 Many thanks

---

### Post by adam814 on 2010-01-18
Out of curiosity is the 40-second slowdown a guess or are you measuring it somehow.  You could install bootchart and see what's actually taking so long in the boot process while getting accurate measurements.

---

### Post by fidelandche on 2010-01-18
What I have been doing to check the boot time is using my watch to time the boot up as I noticed it starting to slow down. Is BootChart via the software centre or the package manager?

---

### Post by adam814 on 2010-01-18
Yeah, the package name is bootchart.  You can get it through Synaptic or apt-get or however you like.

---

### Post by fidelandche on 2010-01-18
Ok thanks for that, any idea on how to speed the system up?

---

### Post by adam814 on 2010-01-18
Short of upgrading RAM I'd run bootchart and see what seems to be taking the most time.  There are some general-purpose tweaks.  I've heard of disabling avahi (although I didn't bother).  If it's a filesystem fsck slowing you down you *could* change the pass value in /etc/fstab to 0, but this has other consequences.

You could profile your boot and see if that makes a difference.  It didn't for me.

---

### Post by fidelandche on 2010-01-18
Ok thanks for that, once I have run bootchart I will post again to see if I can be pointed in the right direction to speed by the laptop.

---

