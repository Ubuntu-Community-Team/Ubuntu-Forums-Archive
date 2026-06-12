---
title: "ubuntu netbook thinks my tv is bigger"
date: 2010-05-28
forum: General Help
---

### Post by peterson2k4 on 2010-05-28
I have an Eeebox b202 running Ubuntu Netbook Edition 9.10 connect to a 42" Samsung Plasma via DVI-HDMI cable. My monitor settings however think my tv is 50" and cuts off the sides.  How can I override the auto detect?

---

### Post by Ampi on 2010-05-28
Try goint to System -> Administration -> System Testing. 

There is a set of test for the monitor where at some point it will check all the resolutions.. 

If not you can always add a resolution in the configuration file  /etc/X11/xorg.conf.
But if you have never done that before, first read a bit more about it so nothing goes wrong.. (or post it here :))

---

### Post by peterson2k4 on 2010-05-28
The system test was not helpful.  I will try to adjust the resolution when I have a chance.  thank you for your help in with this.  I will let you know how it goes. :)

---

### Post by Ampi on 2010-05-30
Apparently 10.04 doesn´t have a xorg.conf file, so my post was useless. But if you do make one it should be read by your system. 
Anyhow, before you do that, here is the link for the wiki on resolution. This might be the best place to start reading.

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

