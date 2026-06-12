---
title: "Trying Ubuntu"
date: 2010-10-02
forum: General Help
---

### Post by ronch79 on 2010-10-02
Hi. I've successfully installed Ubuntu 10.04 on my laptop but I'm having trouble even trying it on my desktop. I tried making both a USB installer and a CD from the .iso image, but when I pop in the CD or insert the USB stick into my desktop and select "Try Ubuntu without making changes to this computer", it manages to get to the chime but nothing is displayed. Apparently the OS hangs up after that or there's a problem with the display. Does this mean Ubuntu will not run on my desktop? I have experienced this not only with Ubuntu 10.04, but other versions too, like Kubuntu 10.04 and Ubuntu 9.04.

Laptop Specs : Acer Aspire 4520, AMD Turion X2 TL-58 (Dual Core 1.9GHz), 2GB DDR2-800, Nvidia 7000M GPU, Nvidia 610M chipset (?), WD 320GB mobile hard disk.

Desktop Specs : AMD Phenom II X3 720, MSI 785GM-E65, 2GB DDR3-1333, ATI HD5670 1GB (Sapphire), Realtek ALC889 audio, WD 1TB Green Power HDD, two LG optical drives, TP-Link TL-WN781N  PCIE Wifi-N adapter. 

Is there any way I can try Ubuntu 10.04 on my desktop without making changes to it? FYI I've successfully installed Ubuntu 10.04 on a laptop using an ATI HD3200 GPU. Thanks in advance.

---

### Post by DeMus on 2010-10-02
> **ronch79 said:**
> Hi. I've successfully installed Ubuntu 10.04 on my laptop but I'm having trouble even trying it on my desktop. I tried making both a USB installer and a CD from the .iso image, but when I pop in the CD or insert the USB stick into my desktop and select "Try Ubuntu without making changes to this computer", it manages to get to the chime but nothing is displayed. Apparently the OS hangs up after that or there's a problem with the display. Does this mean Ubuntu will not run on my desktop? I have experienced this not only with Ubuntu 10.04, but other versions too, like Kubuntu 10.04 and Ubuntu 9.04.

Laptop Specs : Acer Aspire 4520, AMD Turion X2 TL-58 (Dual Core 1.9GHz), 2GB DDR2-800, Nvidia 7000M GPU, Nvidia 610M chipset (?), WD 320GB mobile hard disk.

Desktop Specs : AMD Phenom II X3 720, MSI 785GM-E65, 2GB DDR3-1333, ATI HD5670 1GB (Sapphire), Realtek ALC889 audio, WD 1TB Green Power HDD, two LG optical drives, TP-Link TL-WN781N  PCIE Wifi-N adapter. 

Is there any way I can try Ubuntu 10.04 on my desktop without making changes to it? FYI I've successfully installed Ubuntu 10.04 on a laptop using an ATI HD3200 GPU. Thanks in advance.

The easiest way to try Ubuntu is to go to [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download"), download the iso file, burn it on a cd and boot the computer from the cd-drive. Maybe you have to change something in your bios to make it boot from the cd-drive. When the cd boots choose: Try Ubuntu (without any changes to your system, or similar text) and start having fun.

---

### Post by CharlesA on 2010-10-02
If it craps out after starting X, what happens if you have ctrl + alt + f1?

---

### Post by ronch79 on 2010-10-03
Thanks for the reply.

@DeMus: Yes, that's what I did. The OS already displayed the "Ubuntu" splash screen which indicates that the PC is reading off the flash disk/CD, but after that the screen goes blank and nothing happens after.

@CharlesA: I tried pressing Ctrl+Alt+F1 and the selection menu comes up. When I select "Try Ubuntu.." I can get to the Ubuntu splash screen but after that the OS freezes over, with a blank screen.

---

### Post by CharlesA on 2010-10-03
Hrm, it looks like it's not even loading the OS fully. Normally Ctrl + alt + f1 would get you to a terminal screen.

---

### Post by jokes_finder on 2010-10-03
The same thing here
I have burned the iso image file on a USB flash stick
it worked well on my desktop
but didn't work in the laptop - the same thing happened to u -
so I went to [this page]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")
check it out and tell me if it answered your question

---

### Post by ronch79 on 2010-10-08
Thanks, jokes_finder. I'll check it out. Unfortunately I'm away from my desktop right now. Will post here my results.

---

### Post by mastablasta on 2010-10-08
assuming everyhting is ok with your download, i would say your graphics card needs additional drivers installed to run a desktop environment that you can only install when you install the system.
 
however as it was mentioned before you should be able to get to command line and then enable simple VGA mode to get to the desktop environment.

---

### Post by Peter09 on 2010-10-08
Also check that the CD burned correctly. Burn it at the lowest speed possible. I have had a similar experience with a bad burn of a CD.

---

