---
title: "GNOME and KDE"
date: 2010-09-06
forum: General Help
---

### Post by rockager on 2010-09-06
i've put kde along with gnome on my ubuntu desktop and i sort of like kde (i had never tried kde before). i want to keep both the environments with me but do not want 2 applications doing the same thing( for example konsole and terminal, conqueror and firefox, ktorrent and transmission etc).so can someone be kind enough to compare the default applications in kde and gnome and tell me which ones to keep.
thanks in advance.

---

### Post by WorMzy on 2010-09-06
Compare them yourself. Only you can decide what works for you.

---

### Post by lovinglinux on 2010-09-07
> **WorMzy said:**
> Compare them yourself. Only you can decide what works for you.

I have to agree. Some people like Gnome, some like KDE. Personally, I prefer KDE applications like Kate, Dolphin, but also use some Gnome applications like Meld over Kompare.

Ktorrent is better than Transmission in my opinion, but I prefer qBitTorrent.

What I do is to install a command-line only system, then install kde-minimal and add only the stuff I like from both environments.

---

### Post by rockager on 2010-09-07
how can i install a command line only system?

---

### Post by garvinrick4 on 2010-09-07
> **rockager said:**
> how can i install a command line only system?
Server edition. You can install GUI with kde and gnome and have choice at login to
boot into either. Same with netbook remix and ubuntu-desktop. After you say install remix and get your system set up you sudo apt-get install ubuntu-desktop it will have your system set-up same or installed packages same as the remix.You can go back and forth using changing default in log-in screen. Kind of cool and remix is nice to cruise around internet and kind of fun to use. I look at it like a huge phone not for a smaller screen. Always nice to know your way around any version of Ubuntu any which way. All have same
file system with different GUI. Do not have to waste disk space on new partition is a plus also.

---

### Post by lovinglinux on 2010-09-07
> **rockager said:**
> how can i install a command line only system?

Get the Alternate CD, before clicking the "Install Ubuntu", hit F4 and choose command-line only option. After installing the core system and rebooting, install necessary packages for graphical environment:

```
sudo apt-get install xorg kdm kde-minimal kdeplasma-addons
```

After that reboot or restart kdm and login. Then install only the applications you like.

---

### Post by 3Miro on 2010-09-07
I was thorn between KDE and Gnome for some time. Now I cannot stand either one, I use XFCE only. You might install that one too, to see if you might like it better.

At the end of the day, use whatever you feel like. Also, keep in mind that KDE apps work better with KDE and Gnome apps work better with Gnome. XFCE uses same libraries as Gnome, so in terms of app compatibility, XFCE and Gnome are about the same.

---

### Post by rockager on 2010-09-10
will there be a significant performance boost after installing xfce instead of gnome or kde? i.e significant enough to make changing the whole desktop environment worth the pain.

---

