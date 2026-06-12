---
title: "Unknown driver, Ubuntu wont detect???"
date: 2012-07-04
forum: General Help
---

### Post by abimael08 on 2012-07-04
How can i fix this??



[IMG]http://24.media.tumblr.com/tumblr_m6nug77CTK1rxi2c0o1_1280.png[/IMG]

---

### Post by msammels on 2012-07-04
First of all, kudos on the lovely theme. Secondly - have you tried to enable restricted drivers?

---

### Post by abimael08 on 2012-07-04
> **msammels said:**
> First of all, kudos on the lovely theme. Secondly - have you tried to enable restricted drivers?


Why thank you, thank you, and Umm Im not aware of what you mean, could you explain?

---

### Post by msammels on 2012-07-04
Sure. In "System Settings" click "Restricted Drivers".

---

### Post by abimael08 on 2012-07-04
> **msammels said:**
> Sure. In "System Settings" click "Restricted Drivers".



Im on ubuntu 12.04, No proprietary drivers, I know Im using Intel SandyBridge because It showed before, but I dont know what happened now ( I had to do use Windows for a project and had to do a re-install ).

---

### Post by msammels on 2012-07-04
As far as I'm aware SandyBridge is the make of processor. (Well, not the make, the codename). I take it your graphics are built in?

EDIT: mine is showing the same, and I'm on a very high end graphics card. I'm not sure what you're issue is?

---

### Post by abimael08 on 2012-07-04
> **msammels said:**
> As far as I'm aware SandyBridge is the make of processor. (Well, not the make, the codename). I take it your graphics are built in?

Yes, exactly, built in with Core i3, It showed before, and I dont know if i downloaded a package from Synaptic, and thats why it showed up before but Im trying to figure it out.

---

### Post by msammels on 2012-07-04
Yes, OK, but what exactly is the problem? :)

---

### Post by abimael08 on 2012-07-04
> **msammels said:**
> Yes, OK, but what exactly is the problem? :)
:D Just that its not detecting it, and I would like to figure out how to get Ubuntu to detect

---

### Post by msammels on 2012-07-04
Well, you would need to install the drivers for your particular chip, which you can probably obtain from a quick Google. However, if you can get a resolution that you're happy with (like 1920x1200 or something), and there's no visible problems, be happy it works:D

---

### Post by ubnewbie2 on 2012-07-04
Try installing glxinfo.  From memory, that's what fixed this problem for me.

---

### Post by msammels on 2012-07-04
Also, perhaps if you read [this](http://askubuntu.com/a/136057) as it fixed it for me. Just the section that is highlighted.

---

### Post by abimael08 on 2012-07-04
> **msammels said:**
> Also, perhaps if you read [this]("http://askubuntu.com/a/136057") as it fixed it for me. Just the section that is highlighted.


I got it, Had to sudo apt-get install 'mesautils', then showed up.

Thanks all

---

### Post by msammels on 2012-07-04
Glad, you got it sorted.

---

