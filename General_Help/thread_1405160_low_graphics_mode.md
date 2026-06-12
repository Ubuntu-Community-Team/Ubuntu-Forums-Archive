---
title: "low graphics mode"
date: 2010-02-12
forum: General Help
---

### Post by celticbhoy on 2010-02-12
I need some help to fix my mother in laws laptop.

Basically my father in law was having a look in software store to see what app ubuntu had, just to increase his knowledge. He installed a couple of apps, and then by accident removed one. The problem is he was looking about in all the sections, and he cant remember what section it was from let alone what he removed.

Now when the laptop boots it shows xsplash then goes to a dialog screen which says :-

(EE) open /dev/fb0:no such file or directory

When I click <OK> I get a small menu with 

Run ubuntu in low-graphics mode
Reconfigure graphics
Troubleshoot
Exit to console

Reconfigure does no good, but I can get logged in to text install.

The laptop is an Acer Aspire 3630 and uses SiS graphics.

I tried to install the xserver-xorg-video-sis file but it is already there?

Any help.....

---

### Post by celticbhoy on 2010-02-12
Just a note if I log in to tty1 and then attempt to startx I get the /dev/fb0 error sitting in tty1, and X hangs.

---

### Post by l-x-l on 2010-02-12
Do you have access to a liveCD? Just a thought but maybe you can copy the fb0 from the LiveCD onto the installation's /dev.

Like I said, just a thought.

---

### Post by celticbhoy on 2010-02-12
Will give it a go.

---

### Post by celticbhoy on 2010-02-12
No luck, and no /dev/fb0 folder on the live disk, or any of the other 4 installs I have.

I think this might be an Xserver issue, just need to find out how to re-install the full Xserver?

---

### Post by celticbhoy on 2010-02-12
Just another little bit of info, this is in the startup log.

(WW)SIS(0):xf86UnMapVidMem: cannot find region for [0xb777a000,0x10000]
(WW)SIS(0):xf86UnMapVidMem: cannot find region for [0xb377a000,0x4000000]

Does this help any?

---

### Post by flippo on 2010-02-13
Although I don't have a solution to your problem I can give you some information about it.  
/dev/fb0 is a framebuffer device (its a file automagically created by udev when it detects a device).  Xorg is trying to access your framebuffer and not finding it, for some reason.  I sadly have no idea what that reason is.  

Some things I would consider, although I have no idea if they are on the right path...
Are you sure your /etc/X11/Xorg.conf is using the correct device driver?  
You may consider reconfiguring Xorg.conf and seeing if you have any luck.

---

