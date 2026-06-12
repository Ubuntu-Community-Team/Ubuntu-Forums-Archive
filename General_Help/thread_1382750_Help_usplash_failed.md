---
title: "Help usplash failed"
date: 2010-01-16
forum: General Help
---

### Post by MarcusA on 2010-01-16
Hello

I just tried to boot into ubuntu but it displays this when booting up:

Usplash: Setting mode 1152x864 failed
Usplash: Using mode 1024x768
Ubuntu 9.10 zoran-desktop tty1
zoran-desktop login:


and thats all Im getting, a terminal which Im not good at :confused:

Any clue what Im supposed to do?



Normally my resolution should be 1440x900

---

### Post by MarcusA on 2010-01-16
ttt

---

### Post by MarcusA on 2010-01-16
Ahum

---

### Post by john newbuntu on 2010-01-17
Login first with your userid and password, then type:
sudo init 2

If you are able to get to gnome, check the file /etc/usplash.conf, change the values to:

```
xres=1280
yres=800
```

Then do:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by john newbuntu on 2010-01-17
you may also have to run:
```
sudo update-initramfs -u -k all
```

---

### Post by MarcusA on 2010-01-17
> **john newbuntu said:**
> Login first with your userid and password, then type:
sudo init 2

If you are able to get to gnome


After I type sudo init 2, i just get to zoran@zoran-desktop:~$

:(

Ok, after typing in startx I am finally back in ubuntu with graphics! yay but I see an error called: "OAFIID:GNOME_FastUserSwitchApplet"

Can I delete this thing or should I let that stay?

---

### Post by john newbuntu on 2010-01-17
See towards the end for the answer:
[http://ubuntuforums.org/archive/index.php/t-619767.html](http://ubuntuforums.org/archive/index.php/t-619767.html)

---

### Post by MarcusA on 2010-01-17
Yeah, never mind, gave me some other problems aswell. Just reinstalled everything again.

---

