---
title: "What happened?!?!"
date: 2010-11-07
forum: General Help
---

### Post by thomas.jerald on 2010-11-07
Ok... so i'm still realivly new to linux... and this is my story...
 
after installing ubuntu 10.04, i noticed that my wireless card wasn't working. The card is a Rosewill RNX-N150PC, with a RaLink RT2860 chipset. I started to install ndiswrapper, but never finished because after i rebooted the system when i got done blacklisting the drivers that i was told to, the card worked. Me not wanting to mess it up and not really caring how it worked just that it did work so that i could get my school work done, just left it alone. But now all of the sudden it has stopped working. I tried doing what I did before, and with no luck. I can't even find what the sys and inf files are so that i can actually use ndiswrapper.
 
Can somebody please help me?
 
Thanks,
Jerald

---

### Post by WorMzy on 2010-11-07
ndiswrapper is a kernel module that uses the Windows drivers for a wireless device.

Have a look at this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

As for where you get the .inf/.sys files, download the drivers from the vendor. If they come in a .exe file, use fileroller to extract the contents (like an archive), and the .inf should be in there, along with the .sys. Check section 3.3 on that page I linked for more info.

---

### Post by MooPi on 2010-11-07
Try this instead [http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095")

---

