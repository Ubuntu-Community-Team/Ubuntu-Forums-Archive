---
title: "Middle scroll button is not working as it should"
date: 2009-07-23
forum: General Help
---

### Post by Vignesh S on 2009-07-23
I recently bought an old IBM thinkpad R31 (non wifi model),and for some reason, the middle scroll button isn't working at all. I tried looking for a driver in the synaptic package manager,but no drivers for it were to be found.

---

### Post by Vignesh S on 2009-07-24
<bump>

---

### Post by Vignesh S on 2009-07-24
<bump>

---

### Post by Vignesh S on 2009-07-24
<bump>

---

### Post by Vignesh S on 2009-07-27
<bump>

---

### Post by Vignesh S on 2009-07-28
<bump>

---

### Post by Hobgoblin on 2009-07-28
Usually no reply means nobody knows the answer.

I have an R40 and the middle button "just works".  This is with 8.10 and 8.04 before that.

---

### Post by scouser73 on 2009-08-21
> **Vignesh S said:**
> I recently bought an old IBM thinkpad R31 (non wifi model),and for some reason, the middle scroll button isn't working at all. I tried looking for a driver in the synaptic package manager,but no drivers for it were to be found.

You can do it in Firefox by typing in the address bar **about:config** and changing **general.autoScroll** to **true**.

---

### Post by Vignesh S on 2009-08-22
That really works. Thanks for that, scouser73.Is there any way to get it to work on Google Chrome?

---

### Post by Vignesh S on 2009-10-30
I found how to do it:
[http://learn.clemsonlinux.org/wiki/Laptops:IBM_Thinkpad_R31#My_xorg.conf_file](http://learn.clemsonlinux.org/wiki/Laptops:IBM_Thinkpad_R31#My_xorg.conf_file)

But there is a slight problem, in Ubuntu 9.10, there isn't a xorg.conf file! I can't change something that doesn't exist! That sucks!

I want to put this in my xorg.conf file (once I either make one or if I can find where it is or otherwise):
Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "PS/2"
    Option "Device" "/dev/input/mouse0"
    Option "YAxisMapping" "4 5"
    Option "XAxisMapping" "6 7"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "EmulateWheelButton" "2"
    Option "EmulateWheel" "true"
EndSection
So yeah, any help would be appreciated

---

### Post by Vignesh S on 2009-10-31
<bump> How on Earth do I put stuff into something that doesn't exist?

---

### Post by cariboo on 2009-10-31
Just create an /etc/X11/xorg.conf and add what you need to it.

```
sudo touch /etc/X11/xorg.conf
```

---

### Post by Vignesh S on 2009-11-03
YAY! It worked. I can now scroll with the middle button. Not exactly working with Google Chrome, but that's another story :-).

---

