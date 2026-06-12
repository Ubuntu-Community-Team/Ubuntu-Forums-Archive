---
title: "No Display After botched BURG Install"
date: 2010-11-24
forum: General Help
---

### Post by williamthefifth on 2010-11-24
Hey all, this is my first post, and I did a silly noobish thing. I have been using Ubuntu in various flavors for a little over a year now, and decided to install it alongside my Win7 Install on my desktop. Last week I read about BURG on omgubuntu.co.uk

I am fairly certain I botched the install of burg somehow

Whenever I turn on the computer, there is no display, not Mobo splash screen, not post, no GRUB menu nothing. the Display light is orange, indicating no input detected. 

But I know the OS is loading, I can hear it bootup, I can login, just by pressing enter, then typing my password, then enter again. Once I hear the login screen drum beat, if I turn off the monitor, then turn it on again, I get a super low res display. the driver works, compiz effects work, but everything is at 640 x 480. when I go to system-> preferences-> monitor the display is labeled as unknown and I can't change the resolution.
I can access the BIOS, but the screen still does not detect the input, even if I power cycle the monitor after access the BIOS, so I won't try to change any settings, as I can't see what I am doing. The only reason I know I am in the Bios is that I can press f10 and then y to cause it to reset to default settings and cause a reboot.

My system:
ATi Radeon hd5870
AMD Phenom II X4 3.4 GHz
WD Velociraptor 300 Gb
4 GbRam
ASUS M4A78-E

---

### Post by blueridgedog on 2010-11-24
The symptoms you describe sound more hardware related than OS or software.  If you don't get a POST screen or access to a display in BIOS, then the motherboard or chip-set must not recognize your graphics card.  Can you try another card?  At a minimum, I would remove and re-seat your current card.

---

### Post by williamthefifth on 2010-11-24
Tried it, also reset the CMOS, tried switching ports to all other DVI ports, including the onboard ones, nothing. Now even turning the monitor on and off after I think bootup has reached login will not work to get me that super-low-res display. If I can just get a display input and get into BIOS I am more than willing to reformat the HDD. If you guys got any tricks, for resetting the default display blind, that'd be awesome

---

