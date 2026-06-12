---
title: "Ubuntu sometimes boots straight to a terminal?"
date: 2012-08-04
forum: General Help
---

### Post by bs5765 on 2012-08-04
My apologies if this has been posted before, I did try to search for it.

Sometimes (it seems to be random), Ubuntu will be loading like normal. I'll see the Ubuntu and the 5 dots, but then instead of loading lightDM, it will just be a terminal. I can log in and everything and it connects itself to the internet but I don't know any commands to try to load a GUI.

My workaround has been to 'sudo reboot now' and boot into recovery mode and then select resume boot. Most of the time that works but sometimes it doesn't and it still decides to boot me into a terminal.

Currently I am not using the proprietary Nvidia driver. Unity 3d and flash work just fine without it, plus when I DO install it, it ALWAYS boots to the terminal and I have to reinstall Ubuntu.

Any help would be greatly appreciated!

---

### Post by zero2xiii on 2012-08-04
Hay,

have you tried:
```
startx
```
This usualy start the xorg server if gui boot ahs been diabled, such as on headless servers and such.

I do not have light-dm installed to test a few commands,

but try to tab complete a few light dm commands eg:

start ligh >TAB<
Start dm >TAB<

And such and see if a suitable command (to logic) is listed.

Cherz

---

### Post by bs5765 on 2012-08-04
Thanks, I will try these next time it happens.

---

### Post by Dylan1473 on 2012-08-04
On a conventional install startx might not work. If it doesn't, try enabling the display manager service in Ubuntu. I forget exactly which one is used by default. For me it's

```
sudo service gdm start
```

(restart might work to)

It might be

```
sudo service lightdm start
```

or

```
sudo service lightdm restart
```

That won't solve the problem of what exactly is causing x to fail to boot in the first place, but it should get it started. Assuming I've got the right service, that is.

---

### Post by dcstar on 2012-08-06
> **bs5765 said:**
> My apologies if this has been posted before, I did try to search for it.

Sometimes (it seems to be random), Ubuntu will be loading like normal. I'll see the Ubuntu and the 5 dots, but then instead of loading lightDM, it will just be a terminal. I can log in and everything and it connects itself to the internet but I don't know any commands to try to load a GUI.
..........
Any help would be greatly appreciated!

Perhaps your hardware has not yet fully initialised when Ubuntu is booting?

See if your BIOS has a Hard Disk Delay option that you can set to a few seconds to allow things to settle a bit before the boot process starts.

---

### Post by jemadux on 2012-08-06
or 
```
 sudo invoke-rc.d lightdm restart
```

if says lightdm is not running just change the resart to start

---

