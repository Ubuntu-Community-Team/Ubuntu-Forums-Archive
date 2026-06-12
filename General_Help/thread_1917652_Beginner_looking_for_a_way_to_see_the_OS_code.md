---
title: "Beginner looking for a way to see the OS code"
date: 2012-01-30
forum: General Help
---

### Post by Future Warthog on 2012-01-30
Okay, I'm a brand spankin' new user to Ubuntu, but I catch on quickly. I came from Windows, having used 95, 98, XP, Vista (Uggh), and 7. I have two Windows computers, one running 7, the other XP. I also have Ubuntu installed on the second computer as a secondary OS. I've only had it for about 3 days, but I love it!:D I am also a programmer and I would like to know how to access the system code, just to see what it looks like.

---

### Post by grahammechanical on 2012-01-30
Well, you are now using an Open Source OS so we had better prove that it is indeed open source.

[https://wiki.ubuntu.com/Kernel/SourceCode]("https://wiki.ubuntu.com/Kernel/SourceCode")

Regards.

---

### Post by pbrane on 2012-01-30
There's also [http://www.kernel.org]("http://www.kernel.org") for the Linux kernel. If you are interested in the GNOME desktop, [http://library.gnome.org/]("http://library.gnome.org/") or just GTK in general [http://www.gtk.org/]("http://www.gtk.org/").

---

### Post by Cheesemill on 2012-01-30
You can get the source code for any application in the official Ubuntu repositories.

First enable the source code repositories either by uncommenting the correct lines in /etc/apt/sources.list or by using Synaptic to enable the source code repos.

You can then just use apt-get to download the source code, for example:
```
apt-get source deluge
```Will download the source code for Deluge into the current working directory.

---

