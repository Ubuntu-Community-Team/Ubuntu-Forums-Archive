---
title: "Urgent help booting!!!!"
date: 2010-05-14
forum: General Help
---

### Post by boom2k1 on 2010-05-14
After applying the latest update on my Ubuntu desktop from the update manager, I couldn't boot into the GUI ANYMORE!!!!


I think it might have something to deal with the NVIDIA update?
I am not sure!

I am really freaking out!!

Even the Recovery mode wouldn't boot me into the GUI!

HOw do I fix it!?


the failsafeX Run in failsafe graphic mode didn't work!
-Fatal server error:
no screens found.

---

### Post by NightwishFan on 2010-05-15
9.10? Tell me your Ubuntu version before attempting.

Boot to a netroot prompt in recovery mode, and run this command:
```
jockey-text -e nvidia-185
```

If that does not work, try:
```
dpkg-reconfigure dkms
```

Finally try this:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup1
```

Remember to reboot after each.

---

### Post by boom2k1 on 2010-05-15
Thanks. I upgraded from 9.04 to 10.04 recently. However, it was a recent update that broke it.

---

### Post by NightwishFan on 2010-05-15
Change the one command to:
```
jockey-text -e xorg:nvidia_current
```

---

### Post by boom2k1 on 2010-05-15
Ah. none of it works.


the bootup screen led to the tty1 screen. i could log in using the text mode.

When I attempted startx, I saw
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
FATAL: Module nouveau not found
(EE) [drm] failed to open device
(EE) open /dev/fb0: No such file or directory
(EE) VERSA(0): No valid modes
(EE) Scree(s) found, but none have a usable configuration

Fatal server error:
no screen found

---

### Post by boom2k1 on 2010-05-15
Thanks. 

Even jockey-text -e xorg:nvidia_current
 does not work for me.

Sigh.

---

### Post by NightwishFan on 2010-05-15
Try this:
```
aptitude update && sudo aptitude install xserver-xorg-video-nouveau
```

Then:
```
jockey-text -d xorg:nvidia_current
```

If you are your own user and not root add ```
sudo 
``` in front of these commands.

---

### Post by boom2k1 on 2010-05-15
I received this message:

Unknown driver: xorg:nvidia_current
Use --list to see available drivers


but when I ran
jockey-text --list,
it said
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display warnings. warn(str(e), _gtk.Warning)

---

### Post by NightwishFan on 2010-05-15
That cant be good.. Try:
```
sudo aptitude install ubuntu-desktop && sudo apt-get -f install
```

---

### Post by boom2k1 on 2010-05-15
Thanks.

I remember I tried installing the ubuntu-desktop, but it was already installed.

I remembered removing the xinit and that also uninstalled ubuntu-desktop. I then reinistalled back xinit, ubunut-desktop, and xstart.
However, it still wouldn't work.

I did not try the -f install.

I ran out of patient and reinstalled Ubuntu using the Live Boot CD. The problem could then be fixed with a new installation. Luckily, the items on my home drive were retained.

I was quite shocked that updating the system using the Update Manager had broken my system to a point beyond repairing!

---

### Post by NightwishFan on 2010-05-16
I have never had such an experience myself but I do not doubt it happened to you. I am sorry I could not be of more help.

---

