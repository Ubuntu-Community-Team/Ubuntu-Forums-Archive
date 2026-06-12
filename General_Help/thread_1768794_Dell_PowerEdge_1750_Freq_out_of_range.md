---
title: "Dell PowerEdge 1750 Freq out of range"
date: 2011-05-27
forum: General Help
---

### Post by LinuxGold on 2011-05-27
Just now did a clean install of Ubuntu 11.04 into Dell PowerEdge 1750 using KVM console and 15" monitor.  When booting into Ubuntu, the monitor went "frequency out of range".  After reading Ubuntu forum someone suggested holding left shift while Grub is loading, it wouldn't even budge.  Please advise on how I can get it to load properly?

Thanks,


Scott

---

### Post by LinuxGold on 2011-05-27
> **dangui said:**
> The rays of the setting sun spilt on the lake, the big banyan surrounding silence. Again I stood by the lake, the banyan side. It was surrounded by pieces in the warm orange sun are reminiscent of the flower reminds me of a the most simple, is also the most beautiful I've ever seen in the sun warm flower shop in the land of the lake, park, a shimmering like gem with flowers, grass sparkling...
[www.ebuybus.com](www.ebuybus.com)

Your point is?

---

### Post by LinuxGold on 2011-05-27
I have 4 of PowerEdge 1750 that need to be set up.  This is the only culprit that I am facing right now.

---

### Post by LinuxGold on 2011-05-27
*bump*

---

### Post by LinuxGold on 2011-05-27
Pulling loose jean pants back up.

---

### Post by collisionystm on 2011-05-27
> **LinuxGold said:**
> Just now did a clean install of Ubuntu 11.04 into Dell PowerEdge 1750 using KVM console and 15" monitor.  When booting into Ubuntu, the monitor went "frequency out of range".  After reading Ubuntu forum someone suggested holding left shift while Grub is loading, it wouldn't even budge.  Please advise on how I can get it to load properly?

Thanks,


Scott

Can you get a picture if you eliminate the KVM from the mix? It sounds like your KVM and your monitor do not support the same resolutions. Ubuntu is reading your KVM and choosing an optimal resolution based on that, your monitor simply cannot support it.

You need to put the monitor on, jump into the terminal, and look at this page to set your resolution to 800x600 or 1024x768.

Or get a new monitor

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

---

### Post by LinuxGold on 2011-05-27
> **collisionystm said:**
> Can you get a picture if you eliminate the KVM from the mix? It sounds like your KVM and your monitor do not support the same resolutions. Ubuntu is reading your KVM and choosing an optimal resolution based on that, your monitor simply cannot support it.

You need to put the monitor on, jump into the terminal, and look at this page to set your resolution to 800x600 or 1024x768.

Or get a new monitor

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

This is an Ubuntu server, with no X-Windows installed at all.  It is handled by GRUB.  None of that was found in your link that you sent me.

---

### Post by collisionystm on 2011-05-27
Okay well then google for your answer. Atleast I sent you in the right direction. And it sounds like you answered your own. Change screen resolution in grub

---

### Post by LinuxGold on 2011-05-27
> **collisionystm said:**
> Okay well then google for your answer. Atleast I sent you in the right direction. And it sounds like you answered your own. Change screen resolution in grub

There is no file in my server:

/boot/grub/menu.lst

---

### Post by LinuxGold on 2011-05-27
Solution for KVM console:

1.) Remotely log in, of course.
2.) Edit /etc/default/grub
3.) Uncommet GRUB_GFXMODE= and use resolution that works
4.) Save the file and run update-grub
5.) Reboot

---

