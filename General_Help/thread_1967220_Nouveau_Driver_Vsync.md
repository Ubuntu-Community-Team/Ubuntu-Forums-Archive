---
title: "Nouveau Driver Vsync"
date: 2012-04-27
forum: General Help
---

### Post by lakerssuperman on 2012-04-27
I usually run the proprietary NVIDIA driver on my machines, but when I upgraded one of my machines to 12.04 I decided to see how the Nouveau driver has come along.  Performance seems good.  I have it running two 1920x1080 screens of a Geforce 210 1gb and effects and desktop use seems very smooth.  The one issue I have with this config is tearing.  Compiz vsync is enabled, but tearing persists.  I haven't been able to find much on Google other than people experiencing similar issues.

Does anyone have a clean, simple method to enable vsync with the Nouveau driver, or a link to a good how-to?  Thanks for any help you guys can provide.

---

### Post by mc4man on 2012-04-27
I use nvidia but I believe you do as posted in this bug description, I'll copy here & link the report, suggest you check.
Apparently you need to add an xorg.conf section, if there is no /etc/X11/xorg.conf then create one 

*just use what's in the "code box"*

> 
USERS OF THE NOUVEAU DRIVER:

If you are using the "nouveau" driver for NVIDIA chips, you will need to enable Sync To VBlank support in the driver options because nouveau has it disabled by default. You can do this by editing /etc/X11/xorg.conf and adding:

# For nouveau only:
```
Section "Device"
 Identifier "My Graphics"
 Option "GLXVBlank" "on"
EndSection
```

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/880707)

---

### Post by lakerssuperman on 2012-04-27
Works great, thanks.  I figured there was an xorg.conf setting, I just didn't know what it was.  I also think I looked at that bug report, but must have breezed right passed that part as  I was messing with this way too late at night.

---

### Post by danielcaraj on 2012-05-04
Hi, same problem here. Can someone post your xorg.conf? I need a reference to start. 

First I didn't have an xorg.conf so I created it and added

```
Section "Device"
 Identifier "My Graphics"
 Option "GLXVBlank" "on"
EndSection
```

Nothing happen :(

Thank you in advance!!:guitar:

---

### Post by lakerssuperman on 2012-05-04
Make sure your xorg.conf file is located in your /etc/X11 folder.    You will also have to reboot for these changes to take effect.  Finally, make sure vsync is enabled in your window manager settings.  For Unity, it would be in the Compiz settings.

---

### Post by danielcaraj on 2012-05-05
> **lakerssuperman said:**
> Make sure your xorg.conf file is located in your /etc/X11 folder.    You will also have to reboot for these changes to take effect.  Finally, make sure vsync is enabled in your window manager settings.  For Unity, it would be in the Compiz settings.

Ok thank you for the answer!

So I have to reboot the system completely, no just the X?
I'm using gnome shell now.

---

### Post by lakerssuperman on 2012-05-05
1) Restarting X should do the job, but since you don't have vsync yet I would just reboot the whole system and see what you get.

2) I'm also running Gnome Shell and it has vsync enabled by default.  

3) I usually just reboot my system if I make any changes to the xorg.conf file.

---

### Post by danielcaraj on 2012-05-06
> **lakerssuperman said:**
> 1) Restarting X should do the job, but since you don't have vsync yet I would just reboot the whole system and see what you get.

2) I'm also running Gnome Shell and it has vsync enabled by default.  

3) I usually just reboot my system if I make any changes to the xorg.conf file.

Didn't work :(. Is not a big problem  anyway...

thank you 8)

---

### Post by lakerssuperman on 2012-05-06
One last thing you might try is to place the following lines in your /etc/environment

CLUTTER_PAINT=disable-clipped-redraws:disable-culling
CLUTTER_VBLANK=True

They force Gnome Shell vsync and other vsync related tweaks to be enabled.

---

### Post by danielcaraj on 2012-05-22
> **lakerssuperman said:**
> One last thing you might try is to place the following lines in your /etc/environment

CLUTTER_PAINT=disable-clipped-redraws:disable-culling
CLUTTER_VBLANK=True

They force Gnome Shell vsync and other vsync related tweaks to be enabled.


Hey, sorry for the delay XD. For the moment seems like is working! but maybe is just my perception ¬¬. Tested on Gnome-Shell and Cinnamon ;).

BTW, I installed the proprietary beta and **stable** drivers for N-vidia, they have a lot of bugs with the 6xx series. So for now I recommend the Nouveau drivers XD, even with compiz (Unity) better performance than proprietary drivers.

Thank you very much for your help. Gracias) [IMG]http://i.imm.io/qbJU.gif[/IMG]

---

### Post by lakerssuperman on 2012-05-22
No problem.  Glad you are having success.

---

