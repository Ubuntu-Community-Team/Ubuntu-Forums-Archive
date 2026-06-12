---
title: "Total Freeze in 10.10 when transferring/downloading/installing large files"
date: 2010-12-28
forum: General Help
---

### Post by spiritofjerry on 2010-12-28
Hello,

I recently installed Xubuntu 10.10 and have been loving it!  (Well, aside from the pulseaudio/skype conundrum, which was easily fixed by disabling pulseaudio).  However, I have one major issue that is really annoying me:

When I first downloaded the plethora of updates from Synaptic after a clean install of Meerkat, my OS completely froze as soon as the install finished, so I REISUBed.  From there, things went well until today, when I mounted two external hard drives to transfer large amounts of content between the two.  Whenever I try to transfer large amounts of data (a gigabyte or more) between my two external drives, the OS freeze rears its ugly head again (just as it did that once while Synaptic was doing its update thing).  Mouse doesn't respond or anything, just a frozen screen.  I've tried Ctrl+Alt+ Backspace and Ctrl+Alt+F1 t no avail.  Where should I start looking to resolve this?  I have experienced video driver issues with Xubuntu on another machine in the past, but these freezes occur only when manipulating large amounts of data.

I ran task manager after the first couple of freezes, and I noticed the CPU runs at 100% during these data transfers.  The Thunar process is highlighted yellow from time to time to indicate a change from idle to active, but I didn't think that was necessarily abnormal, considering file creation and manipulation was underway. 

BTW, I have 4GB of swap, and I have a separate partition for Windows XP for a dual boot, and Windows has never given me any problems whatsoever.  I ran memtest today on the RAM, and all checked out OK. Any suggestions what could be causing these Meerkat freezes?

System details:
eMachines EL 1200-06w
1GB RAM
[http://www.emachines.com/products/products.html?prod=EL1200-06w]("http://www.emachines.com/products/products.html?prod=EL1200-06w")

---

### Post by spiritofjerry on 2010-12-28
the only other mention of anything similar to my freeze problem I have found comes from user cburton in this Virtualbox thread: 

[http://forums.virtualbox.org/viewtopic.php?f=3&t=35214&sid=2e6c39b380cbe0d14d469a0c0ca10c9e&start=15#p158983]("http://forums.virtualbox.org/viewtopic.php?f=3&t=35214&sid=2e6c39b380cbe0d14d469a0c0ca10c9e&start=15#p158983")

however, this user experienced the freezes in 10.10 while runnning within the Virtualbox software in XP, so I'm not sure if this is even applicable.

---

### Post by gordintoronto on 2010-12-29
I would disable the screen saver and anything else in Power Management.

1GB is not a lot of data. I recently copied 155 GB to an external hard drive in a single copy operation.

---

### Post by dcstar on 2010-12-29
> **spiritofjerry said:**
> 
..........
Whenever I try to transfer large amounts of data (a gigabyte or more) between my two external drives, the OS freeze rears its ugly head again (just as it did that once while Synaptic was doing its update thing).  Mouse doesn't respond or anything, just a frozen screen.  I've tried Ctrl+Alt+ Backspace and Ctrl+Alt+F1 t no avail.  Where should I start looking to resolve this?  I have experienced video driver issues with Xubuntu on another machine in the past, but these freezes occur only when manipulating large amounts of data.

I ran task manager after the first couple of freezes, and I noticed the CPU runs at 100% during these data transfers.
......

Give this a try:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by vasalx on 2011-01-13
I was also suffering from the freezing issue in new Xubuntu installation, namely during downloading updates with Synaptic (and not even). The problem was caused by wrong graphics configuration.
Solved it by accident: after some manipulation with xorg.conf I was unable to boot - everything stacked at Xubuntu logo. So, I reboot in recovery mode (holding Shift), and changed graphics configuration to its default. Now everything is fine. :)

Cheers!

---

