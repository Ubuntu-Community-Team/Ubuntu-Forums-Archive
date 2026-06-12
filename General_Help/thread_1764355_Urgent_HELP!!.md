---
title: "Urgent HELP!!"
date: 2011-05-21
forum: General Help
---

### Post by lordzed80 on 2011-05-21
Hi All,

    I am a relatively new user Ubuntu 11.04. I just installed this version and i tried to customize it using Compiz. And after i did that, it appears that i have been zoomed in to my desktop and i can not access the sidebar or even the topbar....furthermore i cant access the terminal or anything to reset Ubuntu. I also do not think that i was giving full admin access when i installed 11.04, i think i have the "Custom" setting/access.

Please help me, i dont want to have to completely format my laptop.

Any help will be greatly appreciated

---

### Post by Mr. Shannon on 2011-05-21
You might look at this thread: [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1763005[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1763005") the solution in post #7 worked for what looks like the same or at least a similar problem.  As for getting to a terminal you might be able to right click on the desktop and create a launcher.

---

### Post by flipper T on 2011-05-21
try holding down your windows key and moving your mouse scroll wheel

---

### Post by Hedgehog1 on 2011-05-21
Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...


***The Hedge***

:KS

---

### Post by 3rdalbum on 2011-05-21
Hedge, Control Alt Delete does nothing on Ubuntu since 9.10. You want Alt Printscreen K instead.

---

### Post by Thewhistlingwind on 2011-05-21
> **3rdalbum said:**
> Hedge, Control Alt Delete does nothing on Ubuntu since 9.10. You want Alt Printscreen K instead.


BS, using 10.10 here, and it works fine.

---

### Post by Hedgehog1 on 2011-05-21
> **3rdalbum said:**
> Hedge, Control Alt Delete does nothing on Ubuntu since 9.10. You want Alt Printscreen K instead.

Actually, you do not want **Alt Printscreen K**, that give you only a forced logout. **Control Alt Delete** does give a nice little dialog window with a choice of logout & reboot.

If you are not seeing that UI, you may have customized your system some time ago and are now used to your special layout.

***The Hedge***

:KS

---

### Post by flipper T on 2011-05-21
given that its been 5 hours since op, i think that the term "urgent" may have been lost in translation

---

### Post by lordzed80 on 2011-05-21
A GREAT THANK YOU for all that replied. I have been able to fix it and it has been restored to its old self.

It required me creating a terminal and resetting UNITY and COMPIZ

Again, THANK YOU ALL VERY MUCH!!!:D

---

### Post by 3rdalbum on 2011-05-22
> **Thewhistlingwind said:**
> BS, using 10.10 here, and it works fine.

Ahh sorry, I thought you were talking about Control-Alt-Backspace, the old X kill combination. Control-Alt-Delete does indeed open the "logout" box.

---

