---
title: "Question about system monitoring software"
date: 2009-10-24
forum: General Help
---

### Post by Tapas Bose, India on 2009-10-24
Hallo everybody.
I want to know about system monitoring software. Google gadget, desklet, screenlet, gkrellm are system monitoring software. Is there any other these kind of software? I saw a software in the link [http://gnome-look.org/content/previe...me=Overglossed]("http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed"). What software is this?

---

### Post by MelDJ on 2009-10-24
you can also use the system monitor applet

---

### Post by Tapas Bose, India on 2009-10-24
> **MelDJ said:**
> you can also use the system monitor applet
I have system monitor applet. What about the given link?

---

### Post by MelDJ on 2009-10-24
that is conky [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by mr_steve on 2009-10-24
I could be wrong, but I believe that is a monitoring app called Conky pictured in that screenshot.

---

### Post by danastasio on 2009-10-24
how about lm-sensors?
```
sudo apt-get install lm-sensors hdd-temp sensors-applet && sensors-detect
```

then you'll have to restart your computer, and when you do that, right click on a taskbar (sorry spent all night trying to get Windows 7 to work, and dont have access to ubuntu right now :( )
and choose add. then just do a simple search for hardware or sensors and add the monitoring app. you can right click on the icons to customize it further.

---

### Post by Tapas Bose, India on 2009-10-24
I have lm-sensor. danastasio do you have lm-sensor? Did you got any warning saying lm-sensor is not compatible with karmic? I got a warning. But lm-sensor still working well in my laptop.

---

### Post by Tapas Bose, India on 2009-10-24
This is conky.

---

### Post by danastasio on 2009-10-31
> **Tapas Bose, India said:**
> I have lm-sensor. danastasio do you have lm-sensor? Did you got any warning saying lm-sensor is not compatible with karmic? I got a warning. But lm-sensor still working well in my laptop.

No, (to my knowledge) I've never gotten an error with lm-sensors, but i've had to re-install my system so many times i may not have noticed.

note to self, asking "what does this do" in the kernel directory, is probably a really bad idea.

---

