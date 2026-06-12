---
title: "can't exit gnome"
date: 2010-06-23
forum: General Help
---

### Post by nmobrien4 on 2010-06-23
I've been trying to stop gdm and enter into console mode with no luck. I'm using sudo /etc/init.d/gdm stop. I've done this before but for some reason it isn't working now. When I run the command I get a blank screen with a blinking cursor in the top left. I recently performed an upgrade so I guess that could have broken something. Any ideas?

---

### Post by Woody1987 on 2010-06-23
press ctrl-alt-f1. Enter your log in details and then type: sudo service gdm stop.

---

### Post by nmobrien4 on 2010-06-23
I'm on a laptop and my F* buttons have dedicated functions F1 lowers screen brightness.

---

### Post by Woody1987 on 2010-06-23
try f1-f6.

---

### Post by nmobrien4 on 2010-06-23
Still no luck.

---

### Post by Woody1987 on 2010-06-23
Are you saying that you can't use your F* keys for anything except the predefined functions? So for example you can't alt-f4 to close a program?

---

### Post by nmobrien4 on 2010-06-23
> **Woody1987 said:**
> Are you saying that you can't use your F* keys for anything except the predefined functions? So for example you can't alt-f4 to close a program?


That's correct. I haven't looked for a way around this as I'm not a big user of the f buttons. It hasn't inconvenienced me until now.

---

### Post by Woody1987 on 2010-06-23
Have you tried the recovery mode? Once the menu appears, click continue and it will get you to a terminal screen without gdm running.

---

### Post by nmobrien4 on 2010-06-23
> **Woody1987 said:**
> Have you tried the recovery mode? Once the menu appears, click continue and it will get you to a terminal screen without gdm running.
Yes I can still enter console mode that way. It just bothers me when things don't work like they should. Also I'd like to be able to switch between the two without rebooting.

---

### Post by Woody1987 on 2010-06-24
To be able to switch without rebooting, you need to be able to use the F* keys.

---

### Post by nmobrien4 on 2010-06-26
Well that's not completely true since I've been able to do it in the past with

```
/etc/init.d/gdm stop
```and 

```
/etc/init.d/gdm start
```I'll settle for recovery mode though.

---

