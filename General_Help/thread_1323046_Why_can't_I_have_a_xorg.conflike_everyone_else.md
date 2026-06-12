---
title: "Why can't I have a xorg.conflike everyone else?"
date: 2009-11-11
forum: General Help
---

### Post by gwpritch on 2009-11-11
My laptop has an ATI xpress 200m integrated video chip ( I'm sorry...how was I to know). I am trying to install a minimal desktop system starting with a cli only install so I have to install the appropriate driver which I believe is "radeon". If I just install this driver I get a flickering cli. The only way I can get a usable desktop is using the 'vesa' driver. So I wanted to get a look at the xorg.conf file to see if I could figure out the problem. Of course in 9.10 there isn't one. 
I tried to reconstitute one by 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

but I get nothing. Can anyone suggest why?
Thanks

---

### Post by ZaHACKieL on 2009-11-11
Are you sure you are looking in the correct place? i.e.  /etc/X11/xorg.conf

---

### Post by gwpritch on 2009-11-11
Yup! After I've typed the command it actually pauses as if its doing something, then goes back to the cli prompt. No error messages.But no /etc/X11/xorg.conf either.

---

### Post by rattasongw on 2009-11-11
like who.i also dont have response by typing that into terminal.by the way i dont think there is xorg.conf in etc/x11 nowadays.you have to create in manually.

---

### Post by krakenfury on 2009-11-11
Make sure you have the 'radeon driver installed.
Then make your own very basic xorg.conf by doing:

touch /etc/X11/xorg.conf

then edit with

sudo <editor> /etc/X11/xorg.conf

It should be blank.  Add:


**Section "Device"**
**    Identifier "**ATI xpress 200m**"**
**    Driver     "**radeon**"**
**EndSection**

This worked for me when I did an Arch install a week ago.  I had a different graphics card, but it should still work.

---

