---
title: "Serial mouse does not work"
date: 2009-12-03
forum: General Help
---

### Post by 0xABC123 on 2009-12-03
[SIZE=2]I have a very old serial mouse (10+ yrs). It is a Logitech M-MD15-9F ball mouse with 3 buttons. The PC is at least 7 years old, and it runs xubuntu 9.04.

*cat /dev/ttyS0* prints random characters when I move the mouse or press any mouse buttons. (and the mouse works correctly in Puppy Linux LiveCD)

[quote=mdetect]
/dev/ttyS0
Microsoft
[/quote]

xorg.conf has ttyS0 and Microsoft in mouse section but the mouse just doesn't work.

Running dpkg-reconfigure -phigh xserver-xorg will replace xorg.conf with a new one which doesn't have mouse section at all.

Can you help me, please? How to make the mouse working?
[/SIZE][SIZE=2]
[/SIZE]

---

### Post by 0xABC123 on 2009-12-04
Bump.

The mouse is detected. Data is received (cursor coords, button presses, etc). But how to get X Server do something with the data?

---

### Post by 0xABC123 on 2009-12-05
/var/log/Xorg.0.log had a line which said something about AllowEmptyInput and disabling mouse drivers.

So I added the following to my xorg.conf:
```

Section "ServerFlags"
    Option "AllowEmptyInput" "false"
EndSection

```
And the mouse works. :D

---

