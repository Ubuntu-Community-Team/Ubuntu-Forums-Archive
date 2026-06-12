---
title: "USB flash memory not detected"
date: 2010-10-03
forum: General Help
---

### Post by woodyg on 2010-10-03
Hi,
I've just installed ubuntu 10.04 on a Lenovo Thinkpad Edge. Problem is that it generally doesn't detect the USB memories that I've been trying to use. On two occasions it did in fact detect the flash memory, but it couldn't open/read it for some reason (USB memories works on other computers), but all the other times the USB flash memory didn't even show up in Nautilus. :confused:

I am no techie so I'm not sure how to check what the problem is here. I've been googling it but either it refers to some specific stuff that doesn't cover my case or it simply is too technical for average users like me to understand.

What do I check first and how do I do that?

---

### Post by woodyg on 2010-10-03
the command "lsusb" gives me

[I]Bus 002 Device 003: ID 17ef:4810 Lenovo 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

no more clues there. what else can I try?

---

### Post by woodyg on 2010-10-06
anyone?

---

### Post by dineshs on 2010-10-06
1)Do you have gparted installed? If yes does the device show up under gparted-devices
2)What ubuntu version are you using ?10.04?Try to plugin the device before booting and see if it mounts
3)Have you installed ndiswrapper?See if [this]("http://ubuntuforums.org/showthread.php?t=1559857") is related

---

### Post by woodyg on 2010-10-09
Thanks for replying. I now also noticed that I was affected by the "detected unsupported model" bug, as that error message was popping up on startup. Didn't notice it before for some reason. Anyway, there was just now one of those automatic ubuntu updates which happened to fix that and in the process my USB problems. My USB memory is now detected! Problem hopefully solved. Am just gonna look closer at it so I can be certain.

Thanks anyway!

---

