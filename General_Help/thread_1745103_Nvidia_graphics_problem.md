---
title: "Nvidia graphics problem"
date: 2011-04-30
forum: General Help
---

### Post by megahost on 2011-04-30
I have a couple problems involving my Nvidia graphics card. 

First, while I try to boot up my monitor says "Input signal out of range, change settings to 1600 x 900 - 60Hz" I tried going into the grub loader and changing:

#GRUB_GFXMODE=640x480

to

GRUB_GFXMODE=640x480

This didn't work.
I continuously have this problem throughout the boot of Ubuntu. On the recommended Nvidia graphics driver, it even gets stuck at the splash screen. 

The second problem involved upgrading the graphics card. I have went into the synaptic package manager to find the drivers for it. I have found the latest version, but when I tried to find it in the additional drivers section, it was not there.

Help is appreciated, Cheers :D

---

### Post by megahost on 2011-04-30
bump.

---

### Post by megahost on 2011-04-30
Anyone aware about what's going on? Is there a way I can access the drivers I got from synaptic package manager?

---

### Post by Logan7x3 on 2011-04-30
srry man, i got nothin

---

### Post by Logan7x3 on 2011-04-30
The problem may be because it really isn't a driver... it way be an attribute to the current driver.

---

### Post by megahost on 2011-04-30
> **Logan7x3 said:**
> The problem may be because it really isn't a driver... it way be an attribute to the current driver.

I don't think that's the problem. I've seen some documentation so someone has to know something about it

---

### Post by NoNameWill on 2011-04-30
What Nvidia card? I believe it's the  7300/7400 that are blacklisted in 11.04

---

### Post by megahost on 2011-04-30
> **NoNameWill said:**
> What Nvidia card? I believe it's the  7300/7400 that are blacklisted in 11.04

I have a GeForce 6150SE nForce 430

---

### Post by NoNameWill on 2011-04-30
[http://ubuntuforums.org/showthread.php?t=1742952](http://ubuntuforums.org/showthread.php?t=1742952)


Have you ever tried installing the drivers the way it's mentioned in post number #2?

---

### Post by megahost on 2011-05-01
I saw your link an I was glad to see many people have had the same problem I have. However like they said, it works when you load the version 173, but Nvidia is in version 270. I'm am not sure what's going on right now.

---

### Post by megahost on 2011-05-01
Solved!
This was a very simple fix. Only 2 commands 

> 
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae


Problem is on upgrade, the graphics driver installed the deb package, but not the driver itself.

Source: [http://ubuntuforums.org/showthread.php?t=1741754](http://ubuntuforums.org/showthread.php?t=1741754)

---

