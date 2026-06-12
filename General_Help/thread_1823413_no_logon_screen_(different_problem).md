---
title: "no logon screen (different problem)"
date: 2011-08-12
forum: General Help
---

### Post by bobismeyep on 2011-08-12
Every time I turn on my computer, everything loads up fine until the login screen. Now this is different, because the background shows up and so does the mouse, but the actual login window isn't there. What is going on?

---

### Post by bobismeyep on 2011-08-12
Please! This is very important!

---

### Post by Carnendil on 2012-06-11
I can report the same problem on my Ubuntu 10.04.

It boots and runs up to showing the background, drumbeat sound, and mouse pointer but not login window.

I can change to tty1 (or any or the other five) and have tried stopping, reconfiguring and restarting gdm; tried reconfiguring plymouth; asked for apt-get to fix any broken packages (none), even reconfigured and updated grub (not really necessary).

What I managed to do is to run startx after

```
sudo service gdm stop
```

Compiz working fine there, I know all my files are OK. But no gnome or anything but my desktop background image and a terminal if I do [Ctrl]+[Alt]+[T]. I image there is a way to launch gnome from there, but I don't know how. At least I know that

```
sudo gnome-session -f
```

won't do.

I suspect some (gdm) configuration file has been corrupted, but I have no idea which it might be or how to restore it.

Any help will be very welcomed.

Thank you.

---

