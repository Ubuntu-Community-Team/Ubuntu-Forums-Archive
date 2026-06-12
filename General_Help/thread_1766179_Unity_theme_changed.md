---
title: "Unity theme changed"
date: 2011-05-24
forum: General Help
---

### Post by Lex-Man on 2011-05-24
I turned on my computer this morning and the theme has changed.  The top bar is white and all of the icons have changed?  I using the default Unity configuration does anyone know whats happened?

---

### Post by linuxinstalledfromhdd on 2011-05-24
Not enough detailed information. 

Have you made any changes or installations to your system since you either upgraded it or installed Ubuntu? How did you install Ubuntu, disc, upgrade, wubi, etc?  What kind of computer do you have? As much details as possible so we can try to figure what happened to your system.

---

### Post by FrostDust on 2011-05-28
I've been experiencing the same issue as Lex-Man,> The top bar is white and all of the icons have changedwith it alternating between the default theme and this each time I log in.

I upgraded by putting the 11.04 install disc image onto a USB drive with Unetbootin, and then erasing and overwriting the main 10.10 partition, but leaving the previous /home partition intact and mounting it as the new /home.

I attached the log file of items I've installed since upgrading.

I built this system myself, it has:
[LIST][*]2.8 Ghz Pentium 4[*]Foxconn 650 motherboard[*]2 GB DDR RAM[*]Geforce 6800 GS AGP video card
[/LIST]

Thanks if you're able to figure anything out. Lemme know if you need anymore details.

---

### Post by richardh9936 on 2011-06-10
Me too.  Sometimes it shows the normal Unity black bar with small widgets, and other times it's a white bar, with hollow widgets.  The Ubuntu symbol also changes from white to coloured.

I may have cross-over issues with L-buntu, but I don't know how to remove the L-buntu bits.

---

### Post by cbowman57 on 2011-06-10
Try this [http://ubuntuforums.org/archive/index.php/t-1672174.html](http://ubuntuforums.org/archive/index.php/t-1672174.html)

> There is a good workaround:
Change the following line in the file /etc/xdg/autostart/gnome-settings-daemon:

Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon

to this:

Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

---

