---
title: "GRUB Bootloader menu"
date: 2010-03-09
forum: General Help
---

### Post by manujnaik on 2010-03-09
Hi, I'm new to this forum and was hoping for a little help :). I have Ubuntu and Windows 7 installed side-by-side. When I boot up, it shows me loads of boot options like "generic-memory diagnostics" and other stuff. How can I set it up so that it will show me just Ubuntu 9.10 and Windows 7?

All help is appreciated

--Manu

---

### Post by DeMus on 2010-03-09
> **manujnaik said:**
> Hi, I'm new to this forum and was hoping for a little help :). I have Ubuntu and Windows 7 installed side-by-side. When I boot up, it shows me loads of boot options like "generic-memory diagnostics" and other stuff. How can I set it up so that it will show me just Ubuntu 9.10 and Windows 7?

All help is appreciated

--Manu

Which *ubuntu did you install and how did you do it, in detail?

---

### Post by manujnaik on 2010-03-09
I installed Ubuntu 9.10 from USB on my laptop using the USB installer for windows. Then I just followed the install instructions and...that's pretty much it...btw, thanks for the quick reply

EDIT: The USB installer was from PenDriveLinux.com and it's called Universal-USB-Installer.exe

This is the Link: [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by manujnaik on 2010-03-21
Okay...it's been a LOOOOOOOOOOOOOOOOOOOOOOOOONG time...i'm waiting for a response...anyone please!!

---

### Post by spiky001 on 2010-03-21
I take it you mean the generic 26xxxxx at the beggining?

---

### Post by phen0m on 2010-03-21
The quick and dirty way to do it would be to edit your grub.cfg file (usually */boot/grub/grub.cfg*) you'll probably have to give it write permissions first

```
sudo chmod u+w /boot/grub/grub.cfg
```

and then edit it as the super user

```
gksudo gedit /boot/grub/grub.cfg
```

And take out all the sections you don't want to see.  This file will be overridden every time you update your grub/kernel and you'll have to redo all the steps.  

For a better solution you can check out the files */etc/default/grub* and the files in the folder */etc/grub.d* and try playing with those.

---

