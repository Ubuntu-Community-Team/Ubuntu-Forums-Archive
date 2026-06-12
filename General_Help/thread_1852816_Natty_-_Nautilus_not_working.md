---
title: "Natty - Nautilus not working"
date: 2011-10-01
forum: General Help
---

### Post by rtyb on 2011-10-01
I don't really know what happened. I was just doing usual stuff, when i tried to open my documents, but it just got to the loading part, got stuck there for around 6 seconds, and then seemingly, it crashed. I tried restarting, and i lost my desktop as well, no right click, no icons, no selection, nothing. I really wonder if this is due to an update? I was updating at moment when i wanted to open nautilus but it didn't work.
I've tried seeing system monitor, so far i haven't seen any misbehaving process. Could this be related to the fact that (recently) everytime Flash comes in (such as when using Youtube), i have constant RAM leakages and have to manually kill the plugin-container process before it crashes my machine (i've seen the plugin-container taking as much as 200% of my CPU....)
But whatever...

here is what i get when running nautilus on the terminal
no gksudo nautilus by the way...
```
yerson@Yerson-MBP-Ubuntu:~$ nautilus

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted
yerson@Yerson-MBP-Ubuntu:~$ 

```

---

### Post by papibe on 2011-10-01
Have you installed Gnome Shell or Gnome 3?

What is the nautilus version?
```
$ nautilus --version
```
Regards.

---

### Post by rtyb on 2011-10-01
Actually i was thinking about it, but after reading a bit about it's instability and stuff like that, i decided i'd wait for 11.10 (when they actually implement the Gnome 3 Library).

So no, i haven't

regarding ```
nautilus --version
```
i get the same output
```
yerson@Yerson-MBP-Ubuntu:~$ nautilus --version

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted
yerson@Yerson-MBP-Ubuntu:~$ 

```

---

### Post by papibe on 2011-10-01
Is it possible that may be inadvertently you have added a ppa with gtk3 dependencies?

Check this:
```
$ dpkg -l | grep -i gtk3
```
Regards.

---

### Post by rtyb on 2011-10-01
I do believe so, but seems quite illogic to me. Dunno, Linux's never logic..

```
yerson@Yerson-MBP-Ubuntu:~$ dpkg -l | grep -i gtk3
ii  libcanberra-gtk3-0                    0.28-0ubuntu7~natty1                                           Gtk+ 3.0 helper for playing widget event sounds with libcanberra
ii  libdbusmenu-gtk3                      0.4.3-0ubuntu4                                                 library for passing menus over DBus - GTK+ version
ii  python-aptdaemon.gtk3widgets          0.41+bzr646-0ubuntu2.1                                         Python GTK+ 3 widgets to run an aptdaemon client
yerson@Yerson-MBP-Ubuntu:~$ 

```

---

### Post by papibe on 2011-10-01
libcanberra-gtk3-0 is not in my natty.

Try this:
```
$ sudo apt-get remove libcanberra-gtk3-0
$ sudo apt-get autoclean
$ sudo apt-get autoremove
```
Then try running nautilus again.

Regards.

---

### Post by rtyb on 2011-10-01
I did as you did. Removed libcanberra-gtk3-0, i was actually surprised at seeing it would only free up 377Kb. 

But too bad, it didn't help nautilus
```
yerson@Yerson-MBP-Ubuntu:~$ nautilus

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted
yerson@Yerson-MBP-Ubuntu:~$ 

```

---

### Post by papibe on 2011-10-01
Oops, it may be load it in memory. Try restarting your PC.

Regards.

---

### Post by rtyb on 2011-10-01
Restarted it, yet the same problem .___.   ...

```
yerson@Yerson-MBP-Ubuntu:~$ nautilus

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted
yerson@Yerson-MBP-Ubuntu:~$ 

```

---

### Post by papibe on 2011-10-01
Sorry about that. I'm running out of ideas...

Try recofiguring nautilus:
```
sudo dpkg-reconfigure nautilus
```
If that don't work, try reinstalling it:
```
sudo apt-get install --reinstall nautilus
```

BTW, we can also check for nautilus version like this:
```
$ apt-cache policy nautilus
```
Regards.

---

### Post by rtyb on 2011-10-01
Don't worry Pal, i appreciate that you took some time to try and help me :)):P

But whatever, i haven't and will not do that. I came to the conclusion, that i'm re-installing ubuntu. Besides, several things weren't working, and i long wanted to reinstall, i was just lazy. So even though i will not do what you said, right now, i might, in the future.

In the end, i barely managed to install the Dolphin File Manager, which does run pretty well. I'll just back everything up, and proceed to wipe my hard drive.

Thank  You Again.

---

