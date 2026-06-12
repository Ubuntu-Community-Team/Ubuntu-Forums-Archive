---
title: "No plymouth on startup (Nvidia Ion)"
date: 2011-04-30
forum: General Help
---

### Post by Jose Catre-Vandis on 2011-04-30
Found this post in the Natty Discussion:
[http://ubuntuforums.org/showthread.php?t=1719745&highlight=natty+plymouth&page=3](http://ubuntuforums.org/showthread.php?t=1719745&highlight=natty+plymouth&page=3)
but as it is closed now starting again.

Just installed Xubuntu 11.04 from alternate CD.

I get no plymouth on startup but I do get it on shut down. What I do get on startup is some white and coloured horizontal lines in the top half of the screen, which I guess is plymouth at least trying?

I have the experimental nvidia drivers installed.

I have tried the FRAMEBUFFER=y and adding lines to kernel options to no avail, and also tried the edit proposed by Harry33 in the link above.

Any other suggestions to get plymouth going at startup?

---

### Post by Frogs Hair on 2011-04-30
I have had the same issue in all the Ubuntu releases I've tried using recommended Nvidia drivers.

I found a fix for 10.04 and 10.10 , but have not found anything for 11.04. These so called fixes worked , but the result was not that great .

I plan to wait and see what comes up in the next few weeks. Good Luck !

---

### Post by TiGR on 2011-05-01
It says that there should be some kind of blacklist. But the problem is that blacklist is empty. It has only commented out header.

---

### Post by Jose Catre-Vandis on 2011-05-01
> **TiGR said:**
> It says that there should be some kind of blacklist. But the problem is that blacklist is empty. It has only commented out header.

I have blacklist file on my 10.10 install called:

/etc/modprobe.d/nvidia-graphics-driver.conf

which contains:

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

so I'll need to have a look - see.... :)

[EDIT]

Well, that made not difference so I tried something else. Went back to the nouveau driver, no difference. installed another plymouth theme - solar. Rebooted. Got the solar theme on shutdown but got the text theme on restart followed by three multicoloured lines, so getting somewhere...

Get the feeling that in 11.04 the graphics driver isn't ready for plymouth??

---

