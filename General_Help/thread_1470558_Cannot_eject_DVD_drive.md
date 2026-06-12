---
title: "Cannot eject DVD drive"
date: 2010-05-02
forum: General Help
---

### Post by csh on 2010-05-02
I have a new laptop (Acer Aspire 4745G). Installed Ubuntu 10.04. There is no eject button on the DVD drive itself.

The eject button is on keyboard. I have to press the key on the keyboard to eject the DVD drive. The eject key does work on Windows 7 and during BIOS screen.

However, after I boot into Ubuntu, the eject button stopped working. Why? How to solve this?

---

### Post by Snake231088 on 2010-05-20
I have the same problem with my Acer 5745G.
If you sleep notebook after the eject button work fine. If no you can run command eject in terminal.
I have the problem of battery status?And you?Are you solved?

---

### Post by cryingthug on 2010-05-27
I have applications that hold on to the CD/DVD. I cannot eject them by pushing the button until the application is closed. This happens with Handbrake, Virtualbox, etc..... i don't understand it.

---

### Post by joehms22 on 2010-08-20
In case you haven't found this yet, Insyde has released new BIOS updates through [support.acer.com]("http://support.acer.com/drivers_download.aspx").

This fixes the cd-eject problem, and problems with the battery not displaying in Ubuntu.  You will need Windows or DOS to install these updates, so I hope you did a dual boot, or maybe you could use FreeDOS.

I did the updates and it fixed both of these problems on my Aspire 5745G.

Good Luck
  - Joe

---

### Post by bayvista on 2010-11-20
I had this annoying problem on a desktop and none of the above suggestions worked. However, I found that if I logged off and on, the drive is freed and you can eject.  I suspect that Gnome is holding on to the drive.

---

