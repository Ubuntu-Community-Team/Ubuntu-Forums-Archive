---
title: "Super User"
date: 2010-10-01
forum: General Help
---

### Post by Granddadof10 on 2010-10-01
How do I get into Super User while in a term screen?

It asked, in 8.04 install for a root pw but I never saw a screen asking
during this 10.04...... install?

Second part:  How do I install Java for Firefox?

Many thanks in advance,   John

ps: Am retired from SUN Microsystems and am SOSO glad Ubuntu is out there and working!!!!!

---

### Post by aysiu on 2010-10-01
> **Granddadof10 said:**
> How do I get into Super User while in a term screen?

It asked, in 8.04 install for a root pw but I never saw a screen asking
during this 10.04...... install?

Second part:  How do I install Java for Firefox?

Many thanks in advance,   John

ps: Am retired from SUN Microsystems and am SOSO glad Ubuntu is out there and working!!!!!
```
sudo -i
```

---

### Post by Granddadof10 on 2010-10-01
Boy do I feel dumb about the:  sudo -i   command................THANKS!

I will wait for the second part of my question......

Thanks in advance all,  John  :)

---

### Post by aysiu on 2010-10-01
Paste in ```
sudo apt-get update && sudo apt-get install icedtea6-plugin
``` or if you want Java, Flash, MP3 playback and a bunch of other proprietary formats ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
``` If you prefer the GUI to the terminal, read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Granddadof10 on 2010-10-02
Many thanks for the cut and paste......

They worked just fine!  :)

Now, off to try to find out why my sound is not working
under ANY program?   Am running Realtek ACL662 and
no issues show up during setup or check for driver  :confused:

Have a great day,   John

---

### Post by Dustin2128 on 2010-10-02
> **Granddadof10 said:**
> Many thanks for the cut and paste......

They worked just fine!  :)

Now, off to try to find out why my sound is not working
under ANY program?   Am running Realtek ACL662 and
no issues show up during setup or check for driver  :confused:

Have a great day,   John
KDE or GNOME?

---

### Post by Granddadof10 on 2010-10-02
GNOME I hope...........:)

John

---

### Post by sisco311 on 2010-10-02
> **Granddadof10 said:**
> 
Now, off to try to find out why my sound is not working
under ANY program?   Am running Realtek ACL662 and
no issues show up during setup or check for driver  :confused:

Have a great day,   John

New topic... start a new thread.


Oh, and mark this one as SOLVED.

EDIT:

Thanks!

new thread: [thread]1587072[/thread]

---

