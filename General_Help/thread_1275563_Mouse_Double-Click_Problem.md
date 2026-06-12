---
title: "Mouse Double-Click Problem"
date: 2009-09-26
forum: General Help
---

### Post by chargersfan420 on 2009-09-26
I'm having the same problem as described in the first few posts of [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=390221").  The mouse will register two clicks with only the left button, about half of the time, no matter which program I am using.  Using xev, I find that pressing the left button registers a click event, while releasing the button registers a release event, another click event, and another release event.

It's definitely not a hardware problem, as the mouse works on other computers, and other OS's on this same laptop.  Also, the touchpad does not have this problem, only the mouse.  It's a Logitech VX Nano. 

Other similar threads point to messing with xorg.conf, but I tried and after a reboot, i was stuck in console for a little while.  My question is, do mouse configs still get stored in xorg.conf?  I'm also on the proprietary ati drivers, so i don't like messing with it.  Any other ideas?

Using Jaunty, on 2.6.30-02063003-generic  (also, should i blame the kernel?  I like this one...)

---

### Post by lovinglinux on 2009-09-26
I had the same problem a couple of weeks ago and could only solve this by replacing the mouse. Nevertheless, you could try to plug the mouse to another usb port if you have an usb mouse. This has worked for me for a while.

---

### Post by chargersfan420 on 2009-09-29
I seemed to have solved my problem by disabling USB legacy support in my BIOS.  I don't think this will cause any issues for me, since i don't think I use any USB devices that aren't 2.0 standard.

However, I can't help but wonder how I would fix this if this wasn't an acceptable solution... obviously it's a USB mouse driver problem...?

---

### Post by wd5gnr on 2009-10-13
I don't know if this will help, but some recent upgrade commented out MOST of the mouse and keyboard entries in my xorg.conf file (/etc/X11/xorg.conf) with the comment that they were now handled by "HAL" (hardware abstraction layer). But it had missed some that I'm sure I added manually at some point. So I removed them and restarted X. That appears to have fixed things.

It probably suffices to remove the InputDevice statements in your ServerLayout (I just put # in front of them) but I also #'d out the actual definitions for Keyboard0 and Mouse0 too (the names of my keyboard and mouse).

Seems odd having no input device language in it, but that's progress for you.

Hope that helps you. Very annoying problem.

---

### Post by chargersfan420 on 2009-10-14
Thank you for the suggestion, wd5gnr.  Unfortunately, there is nothing in my xorg.conf related to anything other than a monitor, so that does not help.

It seems that disabling USB legacy support hasn't completely solved the problem, although it has greatly reduced it.

I regularly use GRUB and LILO, because GRUB loses track of my optical drive while booting, and because LILO takes forever, so I think the problem might only exist now while using LILO... I'll have to pay more attention to this to see if it is related to the problem.

---

### Post by wd5gnr on 2009-10-14
Well in all fairness this only REDUCED the problem (although greatly). So now instead of 90% of the clicks getting doubled, maybe 1% get doubled. Infrequent but still annoying.

---

### Post by vasanthraj on 2009-10-24
Hi All,

I recently installed Ubuntu  Jaunty Jackalope in my PC. I have this strange problem with mouse clicks. First when i right click on empty space on desktop, sometimes it auto creates a new folder. On open office calc spreadsheet, when i click on the sheet tab at the bottom it automatically pops up "rename sheet" . Also on the main ubuntu menu bar if i click on the menu, the menudrop down showsand closes fast as if i have doublclicked. I read inforums and shosen "Double click to open items" under folder preferences > behaviour tab. 

Iam sure the  mouse is fine because it works under windows well. Please help. Thanks.

---

