---
title: "Can't change display resolution!"
date: 2010-06-16
forum: General Help
---

### Post by fvanbeijnen on 2010-06-16
Hello,

I am a newbie and I am Dutch, so sorry for my language.
My problem is: I use ubuntu 10.4 LTS with a Samsung Syncmaster 710V, a 17 inch TFT display together with a Nvdia Geforce 6200 Turbo.
Ubuntu sees my display as a 15 inch CRT and so I can't change the resolution to 1280x1024. Who knows the answer?

---

### Post by diesch on 2010-06-16
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution) and [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) may help you

---

### Post by 4chan on 2010-06-16
simply install the recommended/current driver, then create nvidia xconfig with :

sudo nvidia-xconfig

and then

gksu nvidia-settings

choose your desired screen resolution and 'save to x config'

the next time you login, you'll find your gnome panels messed up, to fix it type :

gconftool --recursive-unset /apps/panel && killall gnome-panel

):P

---

