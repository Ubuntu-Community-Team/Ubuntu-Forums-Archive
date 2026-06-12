---
title: "Disable CTRL+SHIFT+ALT+F1!"
date: 2011-05-04
forum: General Help
---

### Post by thexnightmare on 2011-05-04
Dear,
How can I disable CTRL+SHIFT+ALT+F1?
Thx

---

### Post by WorMzy on 2011-05-04
Do you mean the ttys?

[http://ubuntuforums.org/showthread.php?t=1627548](http://ubuntuforums.org/showthread.php?t=1627548)

---

### Post by thexnightmare on 2011-05-04
thx pal, found it, but when i am trying to save, system tell me that i dont have permissions.
How to get those permissions?
Thx

---

### Post by WorMzy on 2011-05-04
If you're using a graphical text editor, like gedit, open it with gksudo:

```
gksudo gedit /etc/init/tty[123456].conf
```

If you're using a command-line editor, like vim, open it with sudo:

```
sudo vim /etc/init/tty[123456].conf
```

---

### Post by thexnightmare on 2011-05-04
dear my friend, thx alot for all ur help.
however, after doing this, and clicking that binding the black screen still appears but this time empty.
how can i fix this?

---

### Post by WorMzy on 2011-05-04
Oh, you want to disable the shortcut completely? Sorry, I misunderstood. You can disable that by adding the DontVTSwitch option to your xorg.conf's ServerFlags section.

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect4]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect4")

So, add

```
Option "DontVTSwitch" "On"
```

inside the ServerFlags section in

```
gksudo gedit /etc/X11/xorg.conf
```

If you don't have that file on your system, you'll need to add it to one of the files in /etc/X11/xorg.conf.d/, I have no idea which one though, so you'll have to check x.org help files (or search google).

---

### Post by thexnightmare on 2011-05-07
thx for your help, however I am still searching where to add the code, as xorg.conf is not found in my system, and still looking for where to add in my ubuntu. hope if you know to tell me.

---

