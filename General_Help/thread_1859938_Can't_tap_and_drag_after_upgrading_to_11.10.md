---
title: "Can't tap and drag after upgrading to 11.10"
date: 2011-10-14
forum: General Help
---

### Post by newspeak on 2011-10-14
Just upgraded and now I can't tap and hold the trackpad to say resize a window or move a scroll bar or drag an icon...the trackpad recognizes taps to execute and the left click button works to perform these tasks...i went into ccsm and checked that all the plugins that relate are enabled...the mouse settings have a tab for trackpad and i can't see anything there that relates to the problem...i am sort of a newb and I am hoping I am just missing something...this is in unity btw

---

### Post by JulesC on 2011-10-16
Hello there,

I've just installed 11.10 and encountered the same problem. After some research, I think I've found the solution. If you know how to do it, just change the following options of the synaptic driver:
FastTaps = 1
SingleTapTimeout = 320

It works quite comfortably for me with these settings. I'm not sure why the default behaviour has been changed though.

If you don't know how to change these, just extract 10-synaptics.conf from the attached file and then put it in /etc/X11/xorg.conf.d/ (you will probably have to create this directory yourself) and then reboot

---

### Post by newspeak on 2011-10-16
> **JulesC said:**
> Hello there,

I've just installed 11.10 and encountered the same problem. After some research, I think I've found the solution. If you know how to do it, just change the following options of the synaptic driver:
FastTaps = 1
SingleTapTimeout = 320

It works quite comfortably for me with these settings. I'm not sure why the default behaviour has been changed though.

If you don't know how to change these, just extract 10-synaptics.conf from the attached file and then put it in /etc/X11/xorg.conf.d/ (you will probably have to create this directory yourself) and then reboot

that worked great...thank you so much

---

### Post by ian_balisy on 2011-10-17
Thank you so much! Very simple fix compared to everything else I was finding online. Worked for me using GNOME Shell, so I think it's not dependent on the interface you're using.

---

### Post by jensbo on 2011-10-18
Thanks a lot. Genius

---

### Post by ernestj on 2011-10-18
can anyone help put this into steps for us newbies?

thanks,
ernie

---

### Post by Carborundum on 2011-10-18
> **JulesC said:**
> Hello there,

I've just installed 11.10 and encountered the same problem. After some research, I think I've found the solution. If you know how to do it, just change the following options of the synaptic driver:
FastTaps = 1
SingleTapTimeout = 320

It works quite comfortably for me with these settings. I'm not sure why the default behaviour has been changed though.

If you don't know how to change these, just extract 10-synaptics.conf from the attached file and then put it in /etc/X11/xorg.conf.d/ (you will probably have to create this directory yourself) and then reboot
You can change these settings yourselves with the 'synclient' command. Changing settings from there doesn't require a reboot.

I am personally a fan of the LockedDrags setting. It makes it so you don't drop the window you're moving if you accidentally let your finger slip off the touchpad. To enable it, just type 'synclient LockedDrags=1' in a terminal.

---

### Post by Carborundum on 2011-10-18
> **ernestj said:**
> can anyone help put this into steps for us newbies?

thanks,
ernie
1. Open a terminal.
2. Type 'man synclient'.
3. Read the documentation to make sure you know what you're doing.
4. Change the settings you are unhappy with, for example:
```
synclient FastTaps=1
synclient SingleTapTimeout=320
synclient LockedDrags=1
```
I personally find 320 ms to be way too long for single tap timeout. I think something around 200 works best.

---

### Post by jensbo on 2011-10-20
Hi, the file by JulesC works for me for the dragging. But I still have an issue with the middle click. I changed it in the config-file, but it does not affect the two finger tapping.

So I added 
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 8, 9, 0, 0, 1, 2, 3
to the startup applications and it works after a restart, but it kind of "forgets" the settings after waking up from suspend.

---

