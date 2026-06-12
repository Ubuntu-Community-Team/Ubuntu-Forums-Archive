---
title: "MSI X320 ubuntu 10.4/10.10 big problem"
date: 2010-11-10
forum: General Help
---

### Post by ivangelion on 2010-11-10
HELLO!! im new here. and im in trouble
i have an msi x320 (damned netbook). it was working with karmic, but no video acceleration and no wireless. 
i decided to update to 10.04 before installing drivers for video and wireless. but all went wrong
each time i boot stuck on blank screen. haged in something
if i did the same in recovery mode stuck in endless:
 mmc2: controller never released inhibit bit (s)
mmc2: card removed during transfer!
mmc2: reseting controller
mmc2: timeout waiting for hardware interrupt

and never get to desktop

i updated to 10.04 and this happened

i loaded 10.10 netbook remix onto my flash drive, and tried to load and make fresh install but no go, very same error

im using my flash drive now with 9.1 netbook remix (dont like it btw) ill use 9.1 desktop later.. to reinstall its working well 

i end up giving up fixin 10. something

ill install 9.1 but i need firs to back up the old home folder, but need to change permision to do it...

can somebody giveme some help how to do this? (i tried chmod command but im doing something wrong cuz nothing happens)

---

### Post by ivangelion on 2010-11-10
some advance. i managed to add a blacklist where blacklisted hcisd and sdhci_pci. the endless loop stoped but i cant reach desktop yet.

---

### Post by ivangelion on 2010-11-10
i changed the live loaded on the pendrive  to desktop 9.1, (has faster nicer interface) im copying now old home folder to external hdd, some files can not be copied due to permission but thanks to the use of sudo nautilus i was able to copy most of the files. 1 hs more ill be checking the back up and then reinstalling 9.1 desktop and putting all back in

---

### Post by ivangelion on 2010-11-11
this really sucks, besides no one looks to be providing some hint or even spam... intalled 9.1 manged to install wifi but no way to make video properly working.  x-org libraries. or something missing each time i try to install from any source i use. finally i endup  messing and uninstalling the whole gui.. fudge ubuntu and msi x320...

---

### Post by ivangelion on 2010-11-11
finally done video and wireless installed 


[http://zusann123.cocolog-nifty.com/b...ernel-updategm]("http://zusann123.cocolog-nifty.com/blog/2010/06/kernel-updategm")


this page helped me. 

thanks for no help forum. hope this will be of help for somebody else

---

### Post by natomasguy on 2010-11-18
I'm having a similar problem trying to get Ubuntu 10.10 installed on an X320.  All I get is scrolling "Controller never released inhibit bit(s)" messages.  Can you explain to me how you got it installed?

---

### Post by sharpy1985 on 2010-11-19
Is everybody trying to install Ubuntu in the MSI X320 this month? I'm having the very same problem and I'm also new here. I did manage to find this online 
[http://wolfs-ubuntu.blogspot.com/2009/06/msi-x320-graphics-installation.html](http://wolfs-ubuntu.blogspot.com/2009/06/msi-x320-graphics-installation.html)
 
it's very helpful but I just installed ubuntu and even with this guide I'm having trouble with the WLAN. can't seem to be able to install the patch utility using apt-get.
 
If anybody can help me out I'd really appreciate it.

---

### Post by giantgreengoat on 2011-05-20
I picked up the uber thin MSI x320 the other day and it is a really nice machine. However, it came with Vista, not good. So, I popped in Natty and attempted an install. Froze. Froze. Froze. I found that I had to add pci=nomsiAppend to the boot script. Worked, but only with Meerkat. Booted. Attempted to install: FAIL. Froze on creating partitions in the install process. I think all of this has to do with the SATA interface. All derivatives, Mint included, of Natty fail at boot regardless of script addition. Errors during boot and hangs. Right now I am getting an ISO of: PCLinuxOS and OpenSuse (Gnome and KDE). Not that the GUI makes a difference since it seems to be a kernel issue. 

Any ideas?

---

### Post by giantgreengoat on 2011-05-20
Got PCLinuxOS to boot and loaded Gparted as root.  Wiped the drive and attempted an install.  Started, but froze as the files were copying over.  I think my issue may lie in faulty equipment.

---

### Post by giantgreengoat on 2011-05-21
Maye it is has something to do with the drive being scsi 3.  Maybe I have to do something different to load/set scsi parameters for successfully reading the drive?

---

### Post by dizzymon on 2011-06-10
I've had my MSI over a year and I basically gave up trying to install ubuntu on it because even installing windows 7 you had to have the drivers for it in order for it to find the hard drive. I have no idea what MSI was thinking when they did this to this netbook. I have NEVER had this much trouble with the ASUS EEE PC's. I'm not sure how well ubuntu runs on this machine but Win 7 runs slow when you type. I've tried IE, Chrome, Firefox. They all run very slow when I type in the google search engine. Not sure if it has to do with googles predictive typing to guess what I'm searching but I am ready to move back to a notebook.

---

