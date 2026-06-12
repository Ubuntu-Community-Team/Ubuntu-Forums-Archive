---
title: "Picture for login screen?"
date: 2010-06-24
forum: General Help
---

### Post by Oolongtea on 2010-06-24
how do I change the login profile picture for the Xubuntu 10.04 login screen. The link below shows a picture that is very similar to the Xubuntu 10.04 login screen. 

[http://picasaweb.google.com/lh/photo/qlFDWN7lTpO2NgqYSdrJnQ-N9AAxCTPJRdDK9ezq6GE?feat=directlink]("http://picasaweb.google.com/lh/photo/qlFDWN7lTpO2NgqYSdrJnQ-N9AAxCTPJRdDK9ezq6GE?feat=directlink")

---

### Post by sisco311 on 2010-06-25
Just copy/move the picture in your home directory and rename it to .face. e.g.:
```
cp /usr/share/pixmaps/faces/penguin.jpg ~/.face
```

[http://library.gnome.org/admin/gdm/2.30/overview.html.en#facebrowser](http://library.gnome.org/admin/gdm/2.30/overview.html.en#facebrowser)

---

### Post by Oolongtea on 2010-06-25
I phrased this question wrong. How do I add a picture for the login screen?

---

### Post by WorMzy on 2010-06-25
Do you mean change the background image?

Press Alt+F2, then run ```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by Oolongtea on 2010-06-25
Nope.....I mean how do I add a profile picture for a user at login. Xubuntu 10.04 doesn't seem to work the same way Ubuntu 10.04 does.

---

### Post by WorMzy on 2010-06-25
Ah, sorry, Just realised that you're using Xubuntu, so that command wouldn't work anyway. I'm not familiar with XFCE or it's related components, but are you sure that what you're asking is possible? That screenshot you posted is Ubuntu Karmic's login screen, running on GDM, not XFCE.

---

### Post by Oolongtea on 2010-06-25
Is there anyway to take a picture of one's login screen? So I may show you what my dilemma is exactly?

---

### Post by Oolongtea on 2010-06-25
There must be a way! I followed the other guys advice and found all these profile avatars and such. They wouldn't be there without a purpose.

---

### Post by WorMzy on 2010-06-25
Well in Ubuntu, you can set your avatar by going to System -> Preferences -> About Me, is there an equivalent menu item to set personal information in on Xubuntu?

---

### Post by Oolongtea on 2010-06-25
In Xubuntu the menu just goes as far as System.

---

### Post by sisco311 on 2010-06-26
> **Oolongtea said:**
> Is there anyway to take a picture of one's login screen? So I may show you what my dilemma is exactly?

Yes. Log out, press Ctrl+Alt+F1 and log in in the virtual console. Run:
```
sudo -u gdm DISPLAY=:1.0 xfce4-screenshooter
```Try DISPLAY=:0.0 or DISPLAY=:2.0 if the command returns a "Cannot open display" error
[noparse]
Press Ctrl+Alt+F7 (or F8) to switch back to the gdm screen and save the screenshot in the /tmp directory.
[/noparse]
Log in.


Here is a screenshot of my login screen:

[[IMG]http://omploader.org/tNHI5eg[/IMG]]("http://omploader.org/vNHI5eg")


My avatar is in my home directory and its filename is .face:

[[img]http://omploader.org/tNHJhNA[/img]](http://omploader.org/vNHJhNA)

---

### Post by Oolongtea on 2010-06-26
Thank you very much for your guys help! I now have a picture for my login screen :) :)

---

