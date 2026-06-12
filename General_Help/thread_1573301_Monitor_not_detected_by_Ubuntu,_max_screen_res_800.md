---
title: "Monitor not detected by Ubuntu, max screen res 800x600"
date: 2010-09-12
forum: General Help
---

### Post by CyanLights on 2010-09-12
Hi everyone,

I just installed the latest Ubuntu Desktop Edition on an old Dell PowerEdge 2300 server as the only operating system. It works beautifully, but no matter what monitor I use, Ubuntu doesn't seem to be able to detect it.

Right now I'm using a Phillips LightFrame 107s, and when using the Monitors dialog, it says the monitor is undetected and the max screen resolution is 800x600, which makes everything terribly cluttered. I don't know if its a driver problem. I've read others having the same issue, but I didn't understand the procedure in installing the driver.

Thank you so much in advance for your help. :)

---

### Post by Lukas666 on 2010-09-12
What video card?

---

### Post by CyanLights on 2010-09-12
> **Lukas666 said:**
> What video card?

I ran this from the terminal after looking it up on google:
```
$ lspci
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X (rev 5c)

```

Of course it listed everything, but I wasn't sure if the other devices were relevant to this or not.

---

### Post by DarthScape on 2010-09-12
Check to see if you need to download the driver for it. System > Administration > Hardware Drivers.

---

### Post by CyanLights on 2010-09-12
> **DarthScape said:**
> Check to see if you need to download the driver for it. System > Administration > Hardware Drivers.
When I open it, it searches for available drivers and the result window is just black and says "No proprietary drivers are in use on this system"

---

### Post by Lukas666 on 2010-09-12
> **CyanLights said:**
> When I open it, it searches for available drivers and the result window is just black and says "No proprietary drivers are in use on this system"

Ok, when you go to System->Administration can you see any ATI related entries? I have NVidia and there is a config program there.

---

### Post by CyanLights on 2010-09-12
> **Lukas666 said:**
> Ok, when you go to System->Administration can you see any ATI related entries? I have NVidia and there is a config program there.
Nope, its just the normal system configuration stuff that comes with Ubuntu.

---

### Post by Lukas666 on 2010-09-12
> **CyanLights said:**
> Nope, its just the normal system configuration stuff that comes with Ubuntu.

Looks like you need an ATI driver.

Could this be any help?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by CyanLights on 2010-09-12
> **Lukas666 said:**
> Looks like you need an ATI driver.

Could this be any help?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Absolutely! :) But, do I use the open or closed source one?  Reading through it, the open source sounds a bit safer.

---

### Post by Lukas666 on 2010-09-12
> **CyanLights said:**
> Absolutely! :) But, do I use the open or closed source one?  Reading through it, the open source sounds a bit safer.

Yeah, start with this one.

---

### Post by deserthowler on 2010-09-12
> **CyanLights said:**
> 

I just installed the latest Ubuntu Desktop Edition on an old Dell PowerEdge 2300 server as the only operating system. It works beautifully, but no matter what monitor I use, Ubuntu doesn't seem to be able to detect it.



I use a Dell C600 Latitude with Win XP for my Magic Jack phone.  I tried Lubuntu 10.04 live CD and couldn't get better resolution than 800x600.  With research, I find the problem is with the new and improved Xorg not supporting older video chips.  I haven't worked more with this problem as I still use the computer for Magic Jack and haven't removed XP.  However, the only solution I can come across is to build xorg.conf file.

Earl

---

### Post by Noz3001 on 2010-09-12
Is the monitor VGA or DVI? VGA doesn't send the monitor's information on my desktop pc so it sticks to 800x600, and I've never found a solution to it apart from plugging it in via DVI

---

### Post by CyanLights on 2010-09-13
> **deserthowler said:**
> I use a Dell C600 Latitude with Win XP for my Magic Jack phone.  I tried Lubuntu 10.04 live CD and couldn't get better resolution than 800x600.  With research, I find the problem is with the new and improved Xorg not supporting older video chips.  I haven't worked more with this problem as I still use the computer for Magic Jack and haven't removed XP.  However, the only solution I can come across is to build xorg.conf file.

Earl

I'm relatively new to all of this. I know Xong is a central system file (used to build /boot/grub/grub.cfg?) but building or changing it seems beyond me. 

[QUOTE=Noz3001]Is the monitor VGA or DVI? VGA doesn't send the monitor's information on  my desktop pc so it sticks to 800x600, and I've never found a solution  to it apart from plugging it in via DVI[/QUOTE]

Its a rather old monitor (rather bulky, to be honest) so I believe its VGA. I don't have any DVI monitors that I could use with that port.

As far as installing the open or closed source ATI driver, its not working for me. The guides seem kinda confusing.

---

### Post by deserthowler on 2010-09-13
> **CyanLights said:**
> I'm relatively new to all of this. I know Xong is a central system file (used to build /boot/grub/grub.cfg?) but building or changing it seems beyond me. 


No, it isn't used to build grub.  It's used for the information for video, keyboard, and mouse.

This is one of those things that just got dumped on Linux for some reason. :twisted: :evil: I'm still looking into this when I have time and will get back when I have some concrete results to share.  Most references I found just say "make a new xorg.conf file and all will be well" or tell you how to generate a useless new one.

The new X works fine if a person doesn't go too legacy.

Earl

---

### Post by CyanLights on 2010-09-14
> **deserthowler said:**
> No, it isn't used to build grub.  It's used for the information for video, keyboard, and mouse.

This is one of those things that just got dumped on Linux for some reason. :twisted: :evil: I'm still looking into this when I have time and will get back when I have some concrete results to share.  Most references I found just say "make a new xorg.conf file and all will be well" or tell you how to generate a useless new one.

The new X works fine if a person doesn't go too legacy.

Earl

I was looking around and stumbled across $ randr, but it doesn't seem to work for me. Theoretically, I should be able to
```
$ randr --output VGA --mode 1024x768
```
But my monitor doesn't seem to even have an output ID.

---

