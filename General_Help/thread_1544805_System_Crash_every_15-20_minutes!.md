---
title: "System Crash every 15-20 minutes!"
date: 2010-08-03
forum: General Help
---

### Post by Unknown-Demon on 2010-08-03
Hi,
As you might have seen in an earlier post, if my PC lags a bit it crashes!
But I wouldn't think it would be an ordinary crash. Earlier today I installed Xubuntu 10.04
onto my PC. Well, The installation was smooth and I was able to get it installed.
I was thinking Thank God it installed!! Then all of a sudden when I was looking around
my PC got caught in a little lag.. And when it lagged this black screen came up and it said
"Starting Common Unix System; cupsd       [ OK ] "
"Checking Battery State   [ OK ] "
Then That screen disappears and these Straight gray bars come up and they cover the top of my screen
And they just blink! I figured it might be a glitch so I went to go eat dinner.
About 20-30 minutes later I come back and there still blinking.
I tryed rebooting the system and trying again and it got cought in a little lag and the
"Starting Common Unix System; cupsd      [ OK ] "
"Checking Battery State   [ OK ] "
Came back up and it disappeared again and the bars came back!
I tried reinstalling Xubuntu 10.04 but it came out the same result.
I tried updating the system cause when I installed it it said I had 164 updates waiting.
It's getting real frustrating! Please HELP!!!!! ;(

_PC INFO_
Dell Dimension 2300 with Xubuntu 10.04 as the operating system
256mbs of RAM
Graphic Card:  VGA compatible controller: Intel Corporation   82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
80 Gig Hard Drive
Dell Moniter 17" 100-200V
_________

---

### Post by Rubi1200 on 2010-08-03
The problem is almost certainly this:
 
> Graphic Card: VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 
Try booting the computer and at the GRUB screen press e to edit and then find the line that ends with > ro quiet splash
Replace quiet splash with i915.modeset=1 and then Ctrl + x to boot.
 
Once you are at the desktop you can try a more permanent solution by looking here:
 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
 
Hope this helps.

---

### Post by HermanAB on 2010-08-03
Hmm, is the CPU cooling fan running?

---

