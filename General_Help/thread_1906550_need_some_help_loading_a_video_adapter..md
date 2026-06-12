---
title: "need some help loading a video adapter."
date: 2012-01-09
forum: General Help
---

### Post by Cammaaron on 2012-01-09
I have a displaylink usb video adapter, I already got the device to work with linux by setting up a xorg.conf file.

However there are two problems I have with it.

One, is that it will not load it by default during bootup. On the config file I said to look in /dev/fb0 and mesg said the usb adapter is in /dev/fb1, and when I change the config file to look in /dev/fb1, mesg says the adapter is in /dev/fb0. This happens all the time, no matter how many times I try it.  I have to manually start x server for it to work, any way to fix this?

Second, snice the driver does not support dragging windows between screen. How do I start a program initially in a different screen?


using ubuntu 11.10

---

### Post by Cammaaron on 2012-01-23
2 weeks and no reply?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!

---

### Post by sudodus on 2012-01-23
Maybe you can make a ***shell script*** with some if statements that checks where it is found and mount it according to that. When you have tested manually that it works, you can make it autostart.

---

### Post by Cammaaron on 2012-01-26
That was what I was thinking, but I have no idea what command to use to do that.

also, any idea what command to use to get programs to appear on a different display.

---

### Post by sudodus on 2012-01-26
> **Cammaaron said:**
> That was what I was thinking, but I have no idea what command to use to do that.

also, any idea what command to use to get programs to appear on a different display.
I suggest that you continue using the commands to look for the usb adapter and to start the X server, but this time in a shell script file.

```
#! /bin/bash 

...
...
...
```

If you start a terminal window in each display, you can use the environment variable DISPLAY to find out what is the address of it.
```
echo $DISPLAY
```
Many application programs have a [FONT="Courier New"][SIZE="3"]-display[/SIZE][/FONT] option, where to enter it.

For example when I run via ssh:
```
xterm -display :0.0
``` I use the display on the server and
```
xterm -display localhost:10.0
``` I use the display on the client.

---

