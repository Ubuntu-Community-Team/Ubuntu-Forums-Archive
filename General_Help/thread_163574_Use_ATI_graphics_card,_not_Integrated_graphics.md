---
title: "Use ATI graphics card, not Integrated graphics"
date: 2006-04-21
forum: General Help
---

### Post by msandersen on 2006-04-21
I've installed an ATI Rage 128 PCI video card into an old 500Mhz Gateway with Intel Integrated Graphics and 320Mb RAM, since Gnome and KDE performance sucks big time on it, moreso Gnome, compared to Windows XP.
Trouble is, whereas the bootup goes through the ATI card, once it's time for the handover to the login screen, the Integrated video port seems to takes over, and the screen goes black save for a static cursor in the top left. The same happens to Windows incidentally. Putting the video cable in the Integrated port gets a blank startup, but gets the image once the login is reached in XP, but not Ubuntu.
I've tested the Ubuntu Live CD, and it does the same, but a Mepis CD doesn't. How do you avoid the Integrated chip taking over? I don't see anything in the BIOS of relevance.

---

### Post by codejunkie on 2006-04-21
[QUOTE=msandersen]I've installed an ATI Rage 128 PCI video card into an old 500Mhz Gateway with Intel Integrated Graphics and 320Mb RAM, since Gnome and KDE performance sucks big time on it, moreso Gnome, compared to Windows XP.
Trouble is, whereas the bootup goes through the ATI card, once it's time for the handover to the login screen, the Integrated video port takes over, and the screen goes black. The same happens to Windows incidentally. Putting the video cable in the Integrated port gets a blank startup, but gets the image once the login is reached.
I've tested the Ubuntu Live CD, and it does the same, but a Mepis CD doesn't. How do you avoid the Integrated chip taking over? I don't see anything in the BIOS of relevance.[/QUOTE]
you should be able to set the bus identifier for the ati card in the xorg.conf file and the xserver will use it instead of the onboard video. open a terminal and enter ```
lspci
```and post the output here.
Edit: since you said your getting nothing but a black screen, it would be kind of hard to do what i asked wouldn't it. since you said it was working with Mepis, boot from the mepis live cd and run the command **lspci** and paste the output here.

---

### Post by msandersen on 2006-04-21
Using the Recover mode, Ubuntu starts up in the console with the ATI card, but if I use "startx", the screen goes black, and I cannot get back to the commandline.

---

### Post by dermotti on 2006-04-21
Disable the onboard vga in the bios. If there is no option in there, it may be a physical jumper on the mainboard you need to move. It should be near the GPU and labled

---

### Post by codejunkie on 2006-04-21
[QUOTE=msandersen]Using the Recover mode, Ubuntu starts up in the console with the ATI card, but if I use "startx", the screen goes black, and I cannot get back to the commandline.[/QUOTE]
press ctrl+alt+F1 to get back to the console.

---

### Post by msandersen on 2006-04-21
Tried ctrl-alt-F1 before. Didn't work. I had a look at this post:
[http://www.ubuntuforums.org/showthread.php?t=94391](http://www.ubuntuforums.org/showthread.php?t=94391)
and tried 
sudo dpkg-reconfigure xserver-xorg
but I broke something.  I only changed to the "ati" driver, and left stuff I didn't knoe the answer to, like the display device.
/var/log/Xorg.0.log ends with:

(II) Primary Device is: PCI 01:08:0
(II) ATI: Candidate "Device" section "ATI AIO Rage 128"
(WW) R128: No matching Device section for instance (BusID PCI:1:8:0) found
(EE) No devices detected.
Fatal error: 
no screens found

Since I'm on the console, I'm not sure how to post the output of the "lspci" command. If you tell me how to direct the output to a text file, I can get to it from a live CD or Windows (via ext2fs).
Or tell me what to look for.

---

### Post by msandersen on 2006-04-21
I'll have a look at the motherboard for a switch later, maybe look for documents on the Gateway site. It's an old computer I've inherited I use for testing so I don't screw up my main computer.

The graphics card is an ATI Rage All-In-One 128
[http://www.ati.com/products/rage128/aiw128/specs.html](http://www.ati.com/products/rage128/aiw128/specs.html)

---

### Post by msandersen on 2006-04-21
I managed to fix it after a bit of tinkering. I used my Mepis CD to compare its working xorg config with Ubuntu's and made some adjustments. It was using the "r128" driver, but I settled on "ati". I might try the other one or research what the difference is. But most importantly, through an error message I found the ATI card needed PCI:1:8:0 in the config, it was on PCI:0:1:0.  I still don't know what it means, but why the hell I need to know this, I also don't know.

3D Graphics is markedly improved over the crappy Intel graphics. Time to switch on some of those nifty 3D screensavers. But Gnome is still disappointingly slow at drawing the screen. I hear 2.14 is much improved in this respect, I'll wait for Dapper to see. I may install KDE to test the difference. The KDE-powered Mepis runs pretty well. Except I don't like KDE very much, apart from its polish.
I haven't tried upgrading Ubuntu yet to a new version, so that might mess things up. Otherwise I may try a complete reinstall to see how the installer has improved and if it recognises and configures the ATI card correctly and use it in preference to the Integrated stuff.
Linux has a very long way to go before it can challenge Windows, even to the standard of Windows 95. And it's nowhere near the old classic Mac OS.

In Windows I disabled the Integrated graphics driver in the Device Manager, so it now boots using the ATI card.

---

