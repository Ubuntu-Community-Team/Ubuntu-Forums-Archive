---
title: "Use X remotely?"
date: 2011-12-17
forum: General Help
---

### Post by Cool Javelin on 2011-12-17
I would like to access my Ubuntu 10.10 headless server (compile programs, etc...,) using graphical interfaces like Lazarus and Geany.

I hear I can interface it via x from other machines on my network (I have an XP machine, and another Ubuntu with Gnome)

I think I can install some kind of x server on the server, then use an x client to have a desktop on a remote machine?

Can someone point me to some good places of info for this?

Thanks, Mark.

---

### Post by lechien73 on 2011-12-17
I've never actually accessed the desktop on a remote X server (I use VNC for that), but you can run on an app-by-app basis by typing:

```
ssh -X username@hostname appname
```

So, to run the Thunar file manager from my home media centre, I can type:

```
ssh -X matt@192.168.0.101 thunar
```

It works wonderfully :)

---

