---
title: "Apply latest Ubuntu Update and no grub menu"
date: 2010-07-01
forum: General Help
---

### Post by gyme2 on 2010-07-01
yesterday, I applied the latest updates from Ubuntu 10.04 which included a kernel update.  Now when I boot my system the 
Grub menu does not show and when I log in I get a terminal window.  Any suggestions on how to fix this problem. Update: I looked in the boot directory and there is no menu.lst file. Not sure why the update did not create a new file.

---

### Post by dschis on 2011-02-03
Same here. I just updated and poof there it went. Tried the shift key during reboot to no avail.
The system does boot. and everything seems to work, but I like to have the grub menu just in case 
I also tried editing it in start up manager, it thought the applicable screens were there ate least according to the GUI, and checking the applicable boxes. Got an output from the terminal that usplash wasn't there. 
I tried to download the usplash via the Synaptic and was told that the dependencies would not be not downloaded. I couldn't even manually download them. 
I also tried to update the grub for the command line, still no menu. 
Any help out there?

---

### Post by wilee-nilee on 2011-02-03
> **dschis said:**
> Same here. I just updated and poof there it went. Tried the shift key during reboot to no avail.
The system does boot. and everything seems to work, but I like to have the grub menu just in case 
I also tried editing it in start up manager, it thought the applicable screens were there ate least according to the GUI, and checking the applicable boxes. Got an output from the terminal that usplash wasn't there. 
I tried to download the usplash via the Synaptic and was told that the dependencies would not be not downloaded. I couldn't even manually download them. 
I also tried to update the grub for the command line, still no menu. 
Any help out there?

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a lot of information without a ton of questions, if your using startup manager your probably multibooting. Don't you think this might be pertinent?

---

