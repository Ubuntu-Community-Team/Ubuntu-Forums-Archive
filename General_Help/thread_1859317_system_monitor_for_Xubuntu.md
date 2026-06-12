---
title: "system monitor for Xubuntu?"
date: 2011-10-13
forum: General Help
---

### Post by rattskjelke on 2011-10-13
Is there an Xfce counterpart of the Gnome System Monitor that will show your processor type, amount of installed memory and Linux kernel version?
All I can find is the Task Manger and it doesn't have a system info tab unless I'm missing something.

---

### Post by Toz on 2011-10-13
Not like the gnome-system-monitor, no. However, you can always install the gnome-system-monitor into xubuntu, it has minimal dependencies.

Other options include conky, gkrellm, sysinfo (look for them in the software centre)

---

### Post by rattskjelke on 2011-10-13
Thanks.
That's what I was afraid of. I just installed Xubuntu 11.10 today and don't want to "Gnomeify" it.

---

### Post by Toz on 2011-10-13
The dependencies for gnome-system-monitor are minimal. On my system, it only installed the following extra packages:

> Start-Date: 2011-10-13  18:38:48
Commandline: apt-get install gnome-system-monitor
Install: gnome-system-monitor:i386 (3.2.0-0ubuntu1), [COLOR="Red"]libwnck-3-0[/COLOR]:i386 (3.2.0-0ubuntu1, automatic), [COLOR="Red"]libwnck-3-common[/COLOR]:i386 (3.2.0-0ubuntu1, automatic)
End-Date: 2011-10-13  18:38:56


---

### Post by rojaasensei on 2011-10-15
sys-info from the main repositories will give the info you are looking for, but it is not part of a task manager

---

