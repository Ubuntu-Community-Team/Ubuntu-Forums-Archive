---
title: "device loading problems"
date: 2010-09-08
forum: General Help
---

### Post by marcusdufrane on 2010-09-08
[sorry i posted this in the wrong spot before so ill try again]

Runnning Ubuntu 8.04 off of a 4GB usb drive.

I am having an intermittent problem with the os loading the touchscreen device.
Most of the time everything loads and works perfectly, but once and a while the touchscreen device doesn't work.

Looking at the log files i think i may have narrowed down part of the problem with in the Xorg log.
it seems that when the device works the driver is loaded and the device is set fine and this message is seen...

elo touchscreen on. local->fd ffffffff..
 After open. local->fd 11(or whatever number is assigned)

and when the device fails this message is present.

elo touchscreen on. local->fd ffffffff..
 After open. local->fd ffffffff
Unable to open elo touchscreen device: No such file or directorycouldn't enable device 4

So, can anyone shed some light on what may be going on here?

---

### Post by harrismh777 on 2010-09-08
Intermittent problems are usually hardware related. But, they can sometimes be timing related... in this case the driver is looking for the device before the hardware ready. However, more likely than not... its an intermittent hardware failure.

Do you have another touch screen you can try temporarily?

Have you checked to see whether there are updates to the driver you are using?

:shock:

---

### Post by marcusdufrane on 2010-09-08
Im leaning towards a timing issue since we were using harddrives and everything was working fine, but after the switch to usb drive this issue popped up. Also it's happening on two touchscreens so i doubt they are both broken.

Any ideas on how to make sure things are ready?

---

### Post by harrismh777 on 2010-09-08
Find the place in the startup script where its doing the insmod on that kernel driver and move it, or put a delay in it.  This may be harder for you (I realize) than I am making it sound.

What happens if you manually unload the module, and the insmod manually?

---

