---
title: "Please helpppp I will be Crazied"
date: 2006-04-15
forum: General Help
---

### Post by iStyle on 2006-04-15
I installed ubuntu 5.10 to my hd.everything was good until I come log on screen.I enter my pass,name and press enter but after a few seconds when it attempt to starting desktop it freeze and I can't move mouse.I don't know what should I do.Pleaseee help me

---

### Post by taurus on 2006-04-15
I think it has something to do with your graphic card.  Reboot and instead of login in at the login screen, press <Ctrl><Atl>F2 to get into a console.  Now, log in with your username and password.  You need to edit your /etc/X11/xorg.conf and replace whatever driver for your video card with vesa.  Type
```

sudo nano /etc/X11/xorg.conf  <-- that is capital x and number eleven, X11...

```
Now, scroll down using the arrow key until you get to the Section "Device" and replace the driver to vesa as
```

Driver               "vesa"

```
Save it by pressing <Ctrl> and x and y to write to it.  Now, either restart X or reboot!  By the way, what is the video card that you have right now in your system?

---

### Post by iStyle on 2006-04-15
thanks it worked i am writing this message from ubuntu.

PS:my graphics card is ati radeon x600 pro

---

