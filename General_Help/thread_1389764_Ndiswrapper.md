---
title: "Ndiswrapper"
date: 2010-01-24
forum: General Help
---

### Post by tacobeans1234 on 2010-01-24
Hello forum,

I'm quite new to the whole "Linux" concept. I just installed Ubuntu using "wubi" and I realized that my PCI network card wasn't supported. I have a Linksys WMP54Gs network card and I already found the .sys and the .inf files that I need. My only problem is installing "Ndiswrapper" to apply said drivers. I downloaded it and I have already moved the .tar.gz file to my ubuntu partition. So my only question is, how do I install it? Also, I don't have any way to access the internet on my ubuntu partition. I'm posting this through the windows side of my HDD. Please go easy on me, It's my first week using Ubuntu.

Thanks for you help! 

--Tacobeans1234

---

### Post by Greenwidth on 2010-01-24
A search for the Linksys WMP54Gs chipset came up as Broadcom BCM4306 which would mean you could use the b43 driver.

Check what chipset you have by typing into a terminal:
```
lspci | grep Network
```

If it is a Broadcom see:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by 73ckn797 on 2010-01-24
If you prefer a graphical way to install the driver, go to System/Administration/Synaptic Package Manager and locate and install "ndisgtk". Then find the driver from the card CD. Typically a Windows XP driver will work. Follow the driver info provided in earlier post here.

---

