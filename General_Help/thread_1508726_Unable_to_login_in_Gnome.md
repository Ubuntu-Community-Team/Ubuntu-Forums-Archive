---
title: "Unable to login in Gnome"
date: 2010-06-13
forum: General Help
---

### Post by Procrat on 2010-06-13
Hi everyone,

I have a problem using Ubuntu 10.04.
When I try to login, the screen turns black or white for a second and then returns to the login screen, without giving any error.
Logging in in tty1 works fine though.

I have already tried some commands that might be of use.
"sudo gdm" gives the following error:
```
/etc/profile: 29: [[: not found

** (gdm-binary:2265): WARNING **: Failed to acquire org.gnome.DisplayManager
** (gdm-binary:2265): WARNING **: Could not acquire name; bailing out
```

"gdmsetup" gives this:
```
(gdmsetup:2272): Gtk-WARNING **: cannot open display:
```

Does anyone have an idea?

---

### Post by Procrat on 2010-06-13
I remember adjusting the /etc/X11/xorg.conf file while I was still using Karmic. I wanted to adjust the screen resolution, which I couldn't do with the GUI. (The screen resolution I wanted wasn't listed.)
So, could this have anything to do with a corrupted xorg.conf file?

---

### Post by Procrat on 2010-06-13
Bump

---

### Post by dino99 on 2010-06-13
actual kernels deal directly with X, so xorg.conf is not needed:

sudo rm -f /etc/X11/xorg.conf

sudo dpkg-reconfigure gdm
sudo rdpkg-reconfigure plymouth

boot without quiet splash to see comments

---

### Post by Procrat on 2010-06-13
Thank you for the quick response! :)

I ran all those commands, but unfortunately it still shows the login screen. One difference is that the resolution is now set to 800x600 or so, but I had expected that when removing xorg.conf...

Er... I didn't know what you meant by "without quiet splash", but after googling a bit, I removed the "quiet splash" and "quiet" bits from /boot/grub/menu.lst. But I don't see any comments now. (Normally I don't see anything before I see my desktop while booting.)

---

### Post by Procrat on 2010-06-14
Bump :)

---

### Post by smellyman on 2010-06-14
[FONT=monospace]Try this:

[/FONT]sudo apt-get install gnome-session

---

### Post by Procrat on 2010-06-14
It can't seem to fetch that package, or any other package for that matter. I think I don't have internet connection...
Any hints about how to establish a wireless connection via tty1?

---

### Post by Procrat on 2010-06-14
Update:
After a reboot, all I see is a black screen with a cursor. (A red cursor, which indicates it's logging in on my user.)
But alas, when I press Ctrl+Alt+F1/F2/F3/F4/F5/F6, I can only see a white blinking cursor in the top left corner and I can't type anything. The only thing I can do, is pressing Alt+Ctrl+Del, which results in a reboot.

Any advice?

---

### Post by delcypher on 2010-06-15
I've found that gdm should be started as a service rather than directly running the command directly.

```

sudo service gdm start #Ubuntu Karmic & Lucid
sudo /etc/init.d/gdm start #Ubuntu 9.04 & lower

```

You can also try the command ```
startx
```

---

### Post by Procrat on 2010-06-23
As I couldn't access the terminal anymore, I didn't see any other possibility than to reinstall Ubuntu with the LiveCD. This solved the problem however!

My screen resolution was reset to 800x600, because my screen wasn't recognised, but a simple command solved that problem. :)
```
sudo X -configure
```

I'll mark this as solved. ^^

---

