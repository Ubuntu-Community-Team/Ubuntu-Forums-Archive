---
title: "cant install sbmanager in 10.04"
date: 2010-05-21
forum: General Help
---

### Post by Highbred8 on 2010-05-21
hi,  im pretty noobish to Linux so sorry if this is a simple task.  i feel like ive tried everything and nothing works.  my iphone connects perfectly, i can view all files (music, vids, pics) that are on it. but it did that out of the box with 10.04, my problem is after installing idevice i tried to install sbmanaget and it never works.

closest i got was using a spanish tutorial on youtube. i dont speak spanish so it was difficult, but it seemed to get the furthest with that. the install gets stuck when trying to run the .autogen.sh command.  

i searched here ,google,youtube and what little i found did not help.

thanks for any help

---

### Post by Highbred8 on 2010-05-21
anyone?

---

### Post by Sheerz on 2010-06-04
I'm assuming you have downloaded the src and are compiling from that.  First of all you need to grab the dependencies needed to build sbmanager:
```
sudo apt-get install build-essential automake autoconf libtool
```
Then cd to the directory you extracted the source and run:
```
sudo ./autogen.sh
sudo make
sudo make install
```
I can't remember every dependency needed to get this to work.  Just use the debug messages you get.  Good luck.  :)

---

### Post by dcstar on 2010-06-05
> **Highbred8 said:**
> hi,  im pretty noobish to Linux so sorry if this is a simple task.  i feel like ive tried everything and nothing works.  my iphone connects perfectly, i can view all files (music, vids, pics) that are on it. but it did that out of the box with 10.04, my problem is after installing idevice i tried to install sbmanaget and it never works.

closest i got was using a spanish tutorial on youtube. i dont speak spanish so it was difficult, but it seemed to get the furthest with that. the install gets stuck when trying to run the .autogen.sh command.  

i searched here ,google,youtube and what little i found did not help.

thanks for any help

[http://translate.google.com/translate?hl=en&sl=es&u=http://120linux.com/sbmanager-ubuntu/&ei=YOIJTLeeNIbZcb237KwO&sa=X&oi=translate&ct=result&resnum=7&ved=0CDoQ7gEwBg&prev=/search%3Fq%3Dsbmanager%2Bubuntu%26num%3D50%26hl%3Den%26newwindow%3D1%26safe%3Doff%26prmd%3Dv](http://translate.google.com/translate?hl=en&sl=es&u=http://120linux.com/sbmanager-ubuntu/&ei=YOIJTLeeNIbZcb237KwO&sa=X&oi=translate&ct=result&resnum=7&ved=0CDoQ7gEwBg&prev=/search%3Fq%3Dsbmanager%2Bubuntu%26num%3D50%26hl%3Den%26newwindow%3D1%26safe%3Doff%26prmd%3Dv)

---

### Post by 206bruce on 2010-06-18
Thanks dcstar!  That link and translation helped.

---

### Post by Grizz Granlien on 2010-12-10
Yes I can't understand the video either and it didn't work I wounder if any one can just upload the thing here and then make it so people can simply click on it to install it
thats if any one is smarty enough

---

