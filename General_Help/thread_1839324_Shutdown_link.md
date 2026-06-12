---
title: "Shutdown link"
date: 2011-09-05
forum: General Help
---

### Post by Lighthorse01 on 2011-09-05
Hi
I have been searching through the forum for a way to create a
link I can put on the desktop so that my older mother can just click
on it and the system will shut down.
does anyone have a menu link I can use on ubuntu 11.04 ??
Thanks

---

### Post by Enigmapond on 2011-09-05
Right-click/Create Launcher (on the desktop), name it "Shutdown", (or whatever), and input this as the command and it will shutdown without asking permission:

```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown
```

---

### Post by philinux on 2011-09-05
Or this.
Right click on an empty part of the top panel. Choose Add to panel.
Scroll down the list and add Shutdown.

---

### Post by raja.genupula on 2011-09-05
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

in that link look for common tasks , that thing gonna help you for not asking password while doing shut down . 

```
sudo shutdown -h 0
```
this is the command for shutdown . 

right click at the desktop to create a  launcher . in that select application in terminal. at the command give the above command . name as shutdown . comment is optional . click OK then . your link is ready .


all the best

---

### Post by Enigmapond on 2011-09-05
I just love Ubuntu. Even with a thing as simple as shutting down...there are many choices.. :)

---

### Post by drs305 on 2011-09-05
> **philinux said:**
> Or this.
Right click on an empty part of the top panel. Choose Add to panel.
Scroll down the list and add Shutdown.

Easiest and requires no password for the default user.  :guitar:

---

### Post by Lighthorse01 on 2011-09-05
Thanks guys I need the link on the desktop so I can make it a little larger for her to know it.
 
Thank you for your help.

---

### Post by drs305 on 2011-09-05
> **Lighthorse01 said:**
> Thanks guys I need the link on the desktop so I can make it a little larger for her to know it.
 
Thank you for your help.

If you can't use the panel option and need to know how to prevent having to input the password when clicking on the Desktop launcher just let us know and we can tell you how to edit the sudoers file.

---

### Post by Enigmapond on 2011-09-05
The command I posted will work great for that. It will shutdown without asking permission using DBus...

---

### Post by drs305 on 2011-09-05
> **Enigmapond said:**
> The command I posted will work great for that. It will shutdown without asking permission using DBus...

I tried it in a VM and it wouldn't work for me, although the shutdown command did. It could be a VM issue. I liked your method and even copied it to my notes to try on my real system when I was ready to shut it down.

---

### Post by Enigmapond on 2011-09-05
Oh right...I don't think that will work via a VM but with a regular installation it works great. The OP didn't mention a VM so that's why I posted it.. :)

Cheers!

---

### Post by drs305 on 2011-09-05
> **Enigmapond said:**
> The OP didn't mention a VM so that's why I posted it.. :)

Cheers!

I'm pretty sure he *isn't* using a VM, but it was the only way I could try it at the time. He/she should have plenty of options now to make mother happy.  ;-)

---

### Post by Enigmapond on 2011-09-05
> **drs305 said:**
> I'm pretty sure he *isn't* using a VM, but it was the only way I could try it at the time. He/she should have plenty of options now to make mother happy.  ;-)
.
:lolflag:

---

### Post by raja.genupula on 2011-09-05
> **drs305 said:**
> Easiest and requires no password for the default user.  :guitar:

thank you !

---

### Post by Lighthorse01 on 2011-09-06
Thanks guys
I just have the regular version of ubuntu 11.04
with unity 2D installed, I want it simple, I could not get any of the above to work except by adding to the top panel. that gave me a nice red shutdown button.
It still asks if you want to shutdown when clicked but at least it is there.

---

