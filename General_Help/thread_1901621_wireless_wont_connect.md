---
title: "wireless wont connect"
date: 2011-12-28
forum: General Help
---

### Post by xedth2 on 2011-12-28
so I did a brand new install of ubuntu 11.04 and took gdm.conf out of the auto start.  but now every time I do a startx and get into the GUI I can see the networks but it won't connect to them.  the network is not secured and when I first installed it I went through and uninstalled gdm and found that this causes my wireless to not function.  I reinstalled and got everything but when I moved gdm.conf it stopped working again.  I know the driver is installed and it should be working but something isn't. is there a service I'm missing the gdm brings up when it auto boots?

thank you

---

### Post by 2F4U on 2011-12-29
Am I right in assuming that NetworkManager is started automatically and that networking is enabled?

---

### Post by xedth2 on 2011-12-29
Yeah, I did a ps -A and outputted them to a file if you want to see them.  But I was able to fix it, the fix, at least to me, doesn't make any sense.  

If I do just a startx and get into the desktop I can't connect but if I do

xinit

which will bring up just a command line in tty7, ctrl-alt-F7, then in there do "gnome-session" it works just fine.  I would love to know why this works.  The only other problem I'm going to have no is the gnome-session command line window is open and don't want to hit it on addictent so going to have to find a way to hide it.

---

### Post by zero2xiii on 2011-12-29
Hay,

Just a suggestion, but if that fixes your problem, why not combine the two seperate commands into one:

```
startx && gnome-session
```

Then you dont have to manualy do it, or why do you have to go to a tty to execute it? Does the gnome-session not work in the normal terminal (ctrl + alt + t)

Cherz

---

### Post by zero2xiii on 2011-12-29
Or,

You can even try to script it all together, and run the script from the terminal instead of startx:

```
!#/bin/bash
startx
gnome-session
#gksudo iw wlan0 up
```

The last line is just to make sure your wireless is up and running.

Intresting situation you have. I have just tried to duplicate the error on my ubuntu 10.04 but I dont have this issue. Startx works fine for me, and then connecting to a wireless network also works directly after that.

Good luck

---

### Post by xedth2 on 2011-12-29
Yeah I'm not sure how exactly I got this so broken.  I've been running into bizarre issues every since I got this netbook for Christmas.  I should also mention I deleted a gdm script in another autoboot somewhere, forget exactly where. Now my sound works in TTY1 but not in the gui so now I have to try and fix that.

I just tried both those ways of launching it.  It doesn't work either way.  I tried replacing all the startx's with xinit and it still doesn't work.

Thanks for the tips though

---

