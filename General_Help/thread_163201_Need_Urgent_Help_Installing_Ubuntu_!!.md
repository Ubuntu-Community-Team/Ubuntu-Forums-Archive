---
title: "Need Urgent Help Installing Ubuntu !!"
date: 2006-04-20
forum: General Help
---

### Post by mubed_007 on 2006-04-20
Hii EveryOne!!
I use MSI RS 480 Motherboard.. Seagate SATA Hdd,, 512 RAM
I just Installed Ubuntu On my HDD
Installation was successfull for sometime After
selecting Partitions etc pc went stand by And After Restarting the pc
When i select uBuntu It Gave Error Like " Failed to start X server (your graphical interface). Its likely that its not setup correctly" I tried to reinstall ubuntu but it gave the same message..
Plz help me what to do??**[B]**[/B]

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=mubed_007]Hii EveryOne!!
I use MSI RS 480 Motherboard.. Seagate SATA Hdd,, 512 RAM
I just Installed Ubuntu On my HDD
Installation was successfull for sometime After
selecting Partitions etc pc went stand by And After Restarting the pc
When i select uBuntu It Gave Error Like " Failed to start X server (your graphical interface). Its likely that its not setup correctly" I tried to reinstall ubuntu but it gave the same message..
Plz help me what to do??**[B]**[/B][/QUOTE]
hit ctrl+alt+f1, login, and do ```
sudo dpkg-reconfigure xserver-xorg
```
you'll usually select the defaults given. if that doesn't work, do above command again, and choose "vesa" when it asks you a driver name for your video card. 
than you'll start X with ```
startx
``` which will automatically start after the next boot. 
what is your video card? make & model

---

### Post by mubed_007 on 2006-04-20
Thanks a lot !!
 I use MSI RS 480 Mothrboard which has onboard graphics card "ATI radeon 2000"

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=mubed_007]Thanks a lot !!
 I use MSI RS 480 Mothrboard which has onboard graphics card "ATI radeon 2000"[/QUOTE]
choose "ati" as the driver name at first. If that doesn't work, choose "vesa".

---

