---
title: "The resolution changes when I log out"
date: 2012-07-13
forum: General Help
---

### Post by EnteRCup on 2012-07-13
Hi.
In  the user selection screen (log out) the resolution changes.
I have 1680x1050 while using Ubuntu, but much smaller resolution while on the log out screen.
Thanks :grin:

---

### Post by Rebelli0us on 2012-07-13
Happens to me, it's the half-baked proprietary video drivers (in my case Intel hd4000 and NVIDIA). I bet if you switch to the open source driver there'll be no problem. For AMD at least the open source video is every bit as good as the flgrxxx#$^&..

---

### Post by jim_deadlock on 2012-07-13
Try editing /etc/lightdm/lightdm.conf and add this line to the end of the file:

```
display-setup-script=xrandr --output default --mode 1024x768
```

Then reboot and see if it works. Did the trick for me.

---

### Post by EnteRCup on 2012-07-13
> **jim_deadlock said:**
> Try editing /etc/lightdm/lightdm.conf and add this line to the end of the file:

```
display-setup-script=xrandr --output default --mode 1024x768
```Then reboot and see if it works. Did the trick for me.
Thanks bro! It works :)! (Just changed the 1024x768 to 1680x1050).

---

