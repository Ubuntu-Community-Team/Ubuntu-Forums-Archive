---
title: "HP webcam - Who developed driver?"
date: 2011-04-20
forum: General Help
---

### Post by tembares on 2011-04-20
Thank you for reading my post.

How can I find out who made the driver for the HP webcam:
temba@Temba-TabletPC:~$ xsetwacom --verbose --list dev
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Power Button' (6).
... Found device 'Video Bus' (7).
... Found device 'Video Bus' (8).
... Found device 'Power Button' (9).
... Found device 'Wacom ISDv4 E3 Finger touch' (10).
Wacom ISDv4 E3 Finger touch TOUCH 
... Found device 'Wacom ISDv4 E3 Pen stylus' (12).
Wacom ISDv4 E3 Pen stylus STYLUS 
... Found device 'Wacom ISDv4 E3 Pen eraser' (11).
Wacom ISDv4 E3 Pen eraser ERASER 
**... Found device 'HP Webcam' (13).**
... Found device 'AT Translated Set 2 keyboard' (14).
... Found device 'HP WMI hotkeys' (16).
... Found device 'SynPS/2 Synaptics TouchPad' (15).

Thank you in advance.

---

### Post by no2498 on 2011-04-21
open a terminal type dmesg click enter
that should tell what driver its trying to use
gives you more to go by

---

