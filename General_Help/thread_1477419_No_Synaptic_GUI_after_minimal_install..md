---
title: "No Synaptic GUI after minimal install."
date: 2010-05-08
forum: General Help
---

### Post by ubunterooster on 2010-05-08
How do I get the synaptic pakage manager front-end?

---

### Post by howefield on 2010-05-08
Probably...

```
sudo apt-get install synaptic
```

---

### Post by ubunterooster on 2010-05-08
tried that already
```
ubunterooster@Rooster:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
ubunterooster@Rooster:~$ 
```I need the GUI, not the preinstalled backend

---

### Post by howefield on 2010-05-08
The package synaptic is the GUI. (As I understood)

[http://packages.ubuntu.com/lucid/synaptic](http://packages.ubuntu.com/lucid/synaptic)

---

### Post by -humanaut- on 2010-05-08
Check aptitude. sudo apt-get install synaptic should install the GUI for apt synaptic isn't a back-end.

---

### Post by ubunterooster on 2010-05-08
Sudo synaptic opened it. How do I edit the xfce menu?

---

### Post by -humanaut- on 2010-05-08
> **ubunterooster said:**
> Sudo synaptic opened it. How do I edit the xfce menu?

You have to create a .gtkrc-2.0 or .desktop file and manually edit it by hand [http://wiki.xfce.org/](http://wiki.xfce.org/) theres no GUI for it

---

### Post by ubunterooster on 2010-05-08
One more thing:

What is the Xfce equivalent of "gksu"?

---

### Post by kerry_s on 2010-05-08
> **ubunterooster said:**
> One more thing:

What is the Xfce equivalent of "gksu"?

it's "gksu" or "gksudo" same as gnome.

---

### Post by mkvnmtr on 2010-05-08
I bet synaptic is on your menu. I think I remember one time on xfce it was under preferiences. Look around for it.

---

### Post by ubunterooster on 2010-05-08
> **kerry_s said:**
> it's "gksu" or "gksudo" same as gnome.
Correct, thank you.
> **mkvnmtr said:**
> I bet synaptic is on your menu. I think I remember one time on xfce it was under preferiences. Look around for it.
It is a "minimal install" that came without even a web browser. I looked at every entry, Synaptic is not listed.

---

