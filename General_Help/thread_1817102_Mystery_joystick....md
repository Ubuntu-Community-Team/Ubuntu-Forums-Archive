---
title: "Mystery joystick..."
date: 2011-08-02
forum: General Help
---

### Post by brianbourke75 on 2011-08-02
I have an HP 8740w laptop and I am trying to hook up my joystick to a game under wine.  Without actually plugging in my joystick I noticed that I already had something under /dev/input/js0.  This is an issue because lots of games look for js0 as the joystick and it's quite a pain to redirect everything to js1. 

I am hoping someone could give me some advice on how to track down what device is being loaded which creates js0 and ultimately disable it.

Cheers!
Brian

---

### Post by brianbourke75 on 2011-08-02
Nevermind, answered my own question.  As it turns out they are selling laptops these days with accelerometers built in to them.  I found this out by looking through the udev log and finding the driver it for what js0 was being loaded with and then hitting the internet and found code which described it in the header.

---

