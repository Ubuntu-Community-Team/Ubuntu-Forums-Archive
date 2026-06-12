---
title: "Bank Screen on Login Acer A-150 Maverick 10.10 UNR"
date: 2010-12-05
forum: General Help
---

### Post by apjonesy on 2010-12-05
Hi Everyone. I have an Acer Aspire 1 A-150 and have UNR 10.10 installed. The machine boots fine and presents me with the login box. However once logged in I just get a black screen, no menu bar or background or icons - the cursor however moves freely around the screen. I also get a graphical box with the shutdown options if I press the off switch . Also the bash sessions Fn 1 to 6 all work fine - its just the graphical interface on f7- a black blank screen. Right clicking doesn't seem to help by giving me any options
Any ideas greatly received - it looks like a problem with x but I'm not sure. 
Thanks in advance

---

### Post by sikander3786 on 2010-12-05
Welcome to the forums :-)

What if you select Ubuntu-Desktop under Sessions in the bottom of your screen on the login screen? That would be visible once you click your user name.

And which graphics card is there? Are the proprietary drivers installed?

---

### Post by apjonesy on 2010-12-05
Thanks Sikander but I have no such option - I am not sure what graphics card but it is the original card supplied with the Acer aspire 1

---

### Post by apjonesy on 2010-12-05
The graphics card is an Intel 945

---

### Post by sikander3786 on 2010-12-05
Ok. From your login screen, press Ctrl + Alt + F1, login using your credentials and try to reconfigure your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot,

```
sudo shutdown -r now
```

Lets see what happens now.

---

