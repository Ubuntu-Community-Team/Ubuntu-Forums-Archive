---
title: "Using ipod with gtkpod"
date: 2005-02-28
forum: General Help
---

### Post by mbaile17 on 2005-02-28
Hello:

I'm new to Ubuntu, though not new to Debian.  I recently installed gtkpod to try to get my ipod working.  Here's the problem:  When I plug in my ipod (via usb) I get the correct "Do not disconnect" warning on the ipod itself but no recognition from my system.  I'm not sure where to find it, in other words (/dev/sda# does not exist) and gtkpod doesn't know where to find it, either.  Any help would be much appreciated!

Thanks,
Meg

---

### Post by astoltz on 2005-03-01
After you plug in the ipod, type "dmesg" at the command line. I'm not at my Ubuntu machine now but it seems like the system dumps lots of messages when the ipod gets plugged in and you should be able to sort out what device node is getting created.  Post the relevent bits of dmesg back here.

It's weird that it's not auto-mounting though, so there may be something else going on.  Are you using Gnome and a standard Ubuntu kernel?

---

