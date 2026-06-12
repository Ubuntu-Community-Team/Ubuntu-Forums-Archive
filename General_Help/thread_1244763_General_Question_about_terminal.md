---
title: "General Question about terminal"
date: 2009-08-19
forum: General Help
---

### Post by audit on 2009-08-19
Why is it that I cannot launch graphical programs from a terminal (tty1) like I can when I am using the gnome-terminal?
 I realize this may not be a question that can be answered in a few words, but if you could direct me to some documentation I would appreciate it.

Thanks in advance

---

### Post by abrari on 2009-08-19
tty is a virtual console. No relation with the GUI. The GUI itself can be started from ttys.
So if you want to launch a GUI-based apps, you need to start Xserver and the display manager first (GDM).
The gnome-terminal itself is a GUI application, so it can run any other GUI apps.
CMIIW.

---

### Post by audit on 2009-08-19
Where do I find out how to start "Xserver" and the display manager?

---

### Post by aysiu on 2009-08-19
> **audit said:**
> Where do I find out how to start "Xserver" and the display manager?
```
startx
``` or ```
sudo /etc/init.d/gdm start
```

---

### Post by bodhi.zazen on 2009-08-19
> **audit said:**
> Why is it that I cannot launch graphical programs from a terminal (tty1) like I can when I am using the gnome-terminal?
 I realize this may not be a question that can be answered in a few words, but if you could direct me to some documentation I would appreciate it.

Thanks in advance

You can if you are running X , you need to specify your display.

```
DISPLAY=:0
xeyes
```

---

### Post by audit on 2009-08-19
Thanks for the help, but I am obviously missing something. Every graphical program I try to run from tty1 will not display.

---

### Post by bodhi.zazen on 2009-08-19
> **audit said:**
> Thanks for the help, but I am obviously missing something. Every graphical program I try to run from tty1 will not display.

Are you getting an error message ?

---

### Post by audit on 2009-08-19
I get the message:

error: Cannot open display

if I type in startx

I get a message telling me it is already running.

---

### Post by aysiu on 2009-08-19
So do ```
sudo /etc/init.d/gdm restart
``` or press Control-Alt-F7

---

### Post by bodhi.zazen on 2009-08-19
You probably need to set the DISPLAY and XAUTHORITY variables.

DISPLAY=:0
XAUTHORITY=/home/your_login_name/.Xauthority

I will look a bit later.

---

### Post by audit on 2009-08-20
If is working--I guess. if I enter
```
firefox --display=:0
```
or 
```
gedit --display=:0
```
and then go back by pressing cntl+alt+f7
I'll find firefox trying to open.
gedit opens but on the terminal I get an error message that is so long I cannot read it. 
either way it is good enough for tonight--thanks so much for all your help.
take care

---

### Post by bodhi.zazen on 2009-08-20
I was close =)

In the console enter :

```
export DISPLAY=:0.0
```

Then you can simply :

xeyes &
firefox &
gedit &

---

### Post by audit on 2009-08-20
```
export DISPLAY=:0.0 
```
did the trick, everything works. 
Thanks for your trouble. Sorry about taking so long to respond I went to sleep.

---

