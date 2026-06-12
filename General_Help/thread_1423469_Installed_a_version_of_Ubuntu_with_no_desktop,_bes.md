---
title: "Installed a version of Ubuntu with no desktop, best way to do these tasks?"
date: 2010-03-06
forum: General Help
---

### Post by thedon_1 on 2010-03-06
Ok so i have a IOn based PC that i use for only xbmc. I previously had a full ubuntu 9.11 install.

I had to reformat the drive but i could not get audio working. I gave the [ION Optimized live CD]("http://forum.xbmc.org/showthread.php?t=66388") a go and it worked with HDMI audio running perfectly.

The thing is when i close xbmc i don't have a desktop, it just goes to command line.

I need to install lirc, copy some keymap files into my xbmc folder and then setup wireless.

What would be the best way? Can it all be done through command line? Can i install a desktop environment?


Thanks

---

### Post by thedon_1 on 2010-03-06
bump

---

### Post by El Zoido on 2010-03-06
Hm, never tried that, but maybe 
```

sudo apt-get install lirc
sudo apt-get install gnome-desktop

```

for the stuff you want to install, the rest I'm not sure.

---

### Post by thedon_1 on 2010-03-07
Tried sudo apt-get install gnome-core

It said gnome-core could not be found, it may be obselete and has been replaced with i think gnome-desktop-data (something like that)

I installed the package it reccomended and hit startx.

I got some blank screen where i could right click and select a few different styles etc but this was a weird desktop, not like Ubuntu's, i couldn't do anything, couldn't go to any files etc. I'm pretty sure it got me into fluxbox.

How do i get my Ubuntu style desktop?

---

### Post by El Zoido on 2010-03-09
Try installing the "ubuntu-desktop" package.

---

### Post by marshag63 on 2010-03-09
Check out this link:

[http://forum.xbmc.org/showthread.php?t=30230](http://forum.xbmc.org/showthread.php?t=30230)

marshaG

---

### Post by thedon_1 on 2010-03-09
Cheers for the link but i don't think there's anything in there that elps me with this problem/

I managed to install gnome but could not get permission to mount the external hd.

It also broke a few things in xbmc so was advised to try another way.

Any suggestions?

---

### Post by thedon_1 on 2010-03-10
bump

---

