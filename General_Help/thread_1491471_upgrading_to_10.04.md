---
title: "upgrading to 10.04"
date: 2010-05-23
forum: General Help
---

### Post by Homunculi on 2010-05-23
was just wondering if the nvidia drivers have been fixed .... 
last time i tried 9.04 there was a glitch ... 

any info would be a big help .... :guitar:
rock on

---

### Post by linuxman94 on 2010-05-23
They should be working just fine in 10.04.  Make sure you use 'Hardware Drivers' in System -> Administration to enable the driver.

---

### Post by Homunculi on 2010-05-23
full open gl drivers ? with sli

---

### Post by Homunculi on 2010-05-27
kewl !! .. working great ... nothing  wen wrong ... added the sli auto to xorg ... 

question tho .. do i need a check in the sli hud in nvidia settings ? that bar just kinda annoying 
:guitar:

rock on

---

### Post by Homunculi on 2010-06-01
this helps in lucid to get the sli mode added  quoting kuritsubaji

I have found something interesting (see next paragraph). I am unsure if my SLI is now fully enabled because I only have one screen and do not use Ubuntu for graphically intense applications (I use Windows for gaming, Linux for everything else).

I had a great deal of trouble in the past getting my Ubuntu/Linux to work with my 2x9600 setup. In the end, the only way I got the manually installed NVidia driver to work on my system was by putting the following lines in the "Driver" Section of my xorg.conf (/etc/X11/xorg.conf):
Code:

Busid "PCI:3:00:00"
Option "sli" "auto"

When I installed 10.04 (clean install), I started to perform my usual manual install of the NVidia driver (my graphics cards are blaringly loud with no driver present, so I can use my computer without 100000000dB of white-noise in the background). The driver install failed. After about an hour of struggling, I said what the h*** and installed the "current" driver that Ubuntu's "Hardware Drivers" GUI prompted me to install (195). It worked! It made my drives quiet, but the /usr/bin/nvidia-settings GUI didn't say it was in SLI mode anywhere.

Today, I tried putting the second line (Option "sli" "auto") in my xorg.conf. After rebooting, my system completed a stable boot. No noticeable difference to me, but I noticed some additions in the nvidia-settings GUI. In the "OpenGL Settings" Section for "X Screen 0", a "Enable SLI Heads-Up-Display" checkbox appeared under the "Miscellaneous" sub-menu.
On both "GPU 0 - (GeForce 9600 GT)" and "1" sections, the main part now has the phrase "(SLI)" appended to the "X Screens:" part - reading "X Screens \t Screen 0 (SLI". "GPU 0" also lists my monitor as a display device, but "Display Devices: \t None" is listed for GPU 1. I expected this difference between GPUs 0 and 1.
EDIT: Without the addition to xorg.conf, GPU 1 claims to have "X Screens: \t None" (yes, bad English on my part). The "Display Devices" section remained unchanged by the xorg.conf addition.

If anyone wants me to run any tests on my computer or has a method for me to use to prove/disprove my SLI is working, let me know. I have added/removed (Option "sli" "auto") to the "Devices" section of my xorg.conf THREE times, and the changes to the nvidia-settings GUI have shown up/disappeared each time.

---

