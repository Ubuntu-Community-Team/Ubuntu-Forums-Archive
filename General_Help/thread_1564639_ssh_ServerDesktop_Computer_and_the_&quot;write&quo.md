---
title: "ssh Server/Desktop Computer and the &quot;write&quot; command"
date: 2010-08-30
forum: General Help
---

### Post by steevven1 on 2010-08-30
I have a computer set up running Ubuntu 10.04. It is being used as both a desktop computer with a mouse, keyboard, and monitor and users running GNOME sessions AND an ssh server for remote command-line access.

Now, when I am remotely accessing this machine via ssh, I see messages sent to me via "write" or "wall" without a problem, as do all other remotely logged in users. However, "writing" to a user or writing to a wall (for example about an upcoming reboot or downtime) does not affect users sitting at the actual computer in GNOME without a Terminal open. How can I get a message to these users, preferably using write and/or wall?

I have root access to this system.

Thanks a lot.

---

### Post by steevven1 on 2010-08-30
Bump?

---

### Post by Bachstelze on 2010-08-31
> **steevven1 said:**
> Bump?

Basically, you get the value of the DISPLAY environment variable for the X display, and then you can run programs on it, so you can display a message with e.g. zenity. Here's a screenshot, hopefully it will make things clear, I have a small screen here. :p

---

### Post by bodhi.zazen on 2010-08-31
You will need to access X

You can use zenity (run these commands as root)

```
export DISPLAY=:0.0
zenity --info --text="System going down in 5 minutes =)"
```

---

### Post by Bachstelze on 2010-08-31
> **bodhi.zazen said:**
> You will need to access X

You can use zenity (run these commands as root)

```
export DISPLAY=:0.0
zenity --info --text="System going down in 5 minutes =)"
```

No need to export, that will just pollute your environment (and might confuse your shell when you try to run other commands).

---

### Post by bodhi.zazen on 2010-08-31
> **Bachstelze said:**
> No need to export, that will just pollute your environment (and might confuse your shell when you try to run other commands).

Could not get it to work without export ;)

> root@bodhi:~#whoami
root
root@bodhi:~#echo $DISPLAY

root@bodhi:~#DISPLAY=:0.0
root@bodhi:~#zenity --info --text="System going down in 5 minutes =)"

[color=darkred][noparse](zenity:13858): Gtk-WARNING **: cannot open display:[/noparse][/color]

root@bodhi:~#export DISPLAY=:0.0
root@bodhi:~#zenity --info --text="System going down in 5 minutes =)"

root@bodhi:~#

---

