---
title: "Motion Eye Webcam doesnt work"
date: 2011-01-13
forum: General Help
---

### Post by Chaosbrain on 2011-01-13
Hi,
I'm a newbie to ubuntu and i recognized that my webcam and my micro doesnt work.
I already read some threads about such problems but didnt get the answers i thought i would...
Could you please help me? 
thx chaosbrain

---

### Post by tredegar on 2011-01-13
Welcome.
What version of ubuntu are you running?
What is your webcam ( **lsusb** should list it)?
What have you used to test it ( I'd recommend you install **cheese** )

---

### Post by Chaosbrain on 2011-01-13
im running 10.04
my hardware:
sony vaio vgn fz21s
cpu: intel centrino duo 2.2 ghz
graphics: nvidia geforce 8600m gs
RAM: 2gb

i already tried it with cheese, empathy, pidgin and skype but without succeed...
thats what the terminal said:  Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]

---

### Post by Quackers on 2011-01-13
If it's a vaio, it may possibly have the r5u87x chipset (the camera). If it has, this worked for me :-)
[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

See supported hardware lower down, then if yours is there (mine's vcc6) just follow the steps (1 to 4) in the terminal.
Then install and run Cheese, if you haven't already.

---

### Post by Chaosbrain on 2011-01-13
THANKS very much that worked :)
but i still have a problem  with my microphone...
could you also help me with that?

---

### Post by Quackers on 2011-01-13
Sorry, but I don't even know if mine works! I've never tried it :-).
I'm sure somebody with the right ideas will be along soon :-)
Glad the camera is working anyway :-)

---

### Post by Chaosbrain on 2011-01-13
okay i hope so ;)
thanks very much again for that quick answer! :)

---

### Post by Quackers on 2011-01-13
You're welcome :-)
This will stop your thread disappearing from the first page - for a while :wink:

---

### Post by Chaosbrain on 2011-01-14
hi again :)

my microphone does work now...
my webcam also, but its quality is veeeery bad... the video is at about 1 fps and its very bright... simply said its not tolerable :(
can you pls help me?

---

### Post by Chaosbrain on 2011-01-19
is there really nobody who can help me? :(
the webcam did a good job about two days ago but when i started it again yesterday it was horrible again. what am i doing wrong? i didnt change anything...

---

### Post by Quackers on 2011-01-19
I don't know why that may be. It may be worth posting in the Hardware & Laptops section as people there may have more experience with built-in webcams.
Good luck.

---

### Post by tonye499 on 2011-01-23
Try (start menu), (all programs), (vaio video&photo suite), (vaio content exporter), that will bring up arcsoft webcam companion, then click on either capture or monitor.

---

