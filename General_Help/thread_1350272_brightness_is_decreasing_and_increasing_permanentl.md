---
title: "brightness is decreasing and increasing permanently in ubuntu 9.10"
date: 2009-12-09
forum: General Help
---

### Post by astecs on 2009-12-09
brightness is decreasing and increasing permanently in ubuntu 9.10 netbook remix. i updated but it continues to do this and it makes me crazy please help me!

---

### Post by gradinaruvasile on 2009-12-09
What hardware do you have? 
Is there a light sensor?

---

### Post by HomoGleek on 2009-12-09
Is this an MSI wind notebook?

---

### Post by Zorael on 2009-12-09
Launchpad: [brightness is broken on MSI WIND U100](https://bugs.launchpad.net/bugs/415023)

And semi-related; [uvcvideo module makes "cannot reset port" error on usb with bison webcam (5986:0203): USB and suspend fails](https://bugs.launchpad.net/bugs/435352)

---

### Post by HomoGleek on 2010-02-11
Bringin up and old thread but I notice no fix has come through the update manager for this.

XP is starting to get so slow on this netbook, anybody know a Linux distro that will work on it? Wind U100.

---

### Post by Anxious Nut on 2010-02-11
> **HomoGleek said:**
> Is this an MSI wind notebook?
+1

my brother has the same problem. but he says that the following works with him:
> **1st method:**
-Switch to a virtual terminal (by pressing Ctrl+Alt+F1)
-Switch back to X11 (by pressing Ctrl+Alt+F7, sometimes Ctrl+Alt+F9).
**2nd method(If the 1st didn't work):**
-Switch to a virtual terminal (by pressing Ctrl+Alt+F1)
-Close the lid of your netbook and wait for at least 5 secs. then open it again.
-Switch back to X11 (by pressing Ctrl+Alt+F7, sometimes Ctrl+Alt+F9).
[COLOR="Red"]Note:[/COLOR] Closing the lid should only put a blank screen in order to make this work, if yours puts it to sleep then change it to blank screen.

**If it stops the craziness when you switch to X11, don't increase the brightness in X11, go back to a virtual terminal and increase it there then go back to X11.**
I hope this works with you as well

---

### Post by Ubunthree on 2010-02-12
Another way which has worked for me:

Right-click anywhere where it will bring up a context menu, like on the control panel along the top, and hold it for a few seconds until the flickering stops. The brightness notification thingie should go away a few seconds later. I've heard it has something to do with improper management of a keyboard buffer or something.

---

