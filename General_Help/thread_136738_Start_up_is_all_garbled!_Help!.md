---
title: "Start up is all garbled! Help!"
date: 2006-02-26
forum: General Help
---

### Post by kurono on 2006-02-26
Hi. This is my first time trying out Linux and I've heard ubuntu was a good place to start.

I installed ubuntu on my IBM Thinkpad R51 laptop and everything went fine. However, when I boot it up, the entire screen is garbled up. I can see and move my mouse cursor, but everything else in the background is garbled up, (blue, white, some gold, black); they looked like strands. I don't know what the problem is.

These are my laptop's specs:
IBM Thinkpad R51
Pentium M 1.5ghz
512 DDR RAM
ATI Mobility Radeon 7500
Onboard Sound
Intel Wireless Adaptor (B/G)

That's all I can remember for the specs off the top of my head.

I'd appreciate any help. Thanks. :)

---

### Post by dcstar on 2006-02-27
[QUOTE=kurono]Hi. This is my first time trying out Linux and I've heard ubuntu was a good place to start.

I installed ubuntu on my IBM Thinkpad R51 laptop and everything went fine. However, when I boot it up, the entire screen is garbled up. I can see and move my mouse cursor, but everything else in the background is garbled up, (blue, white, some gold, black); they looked like strands. I don't know what the problem is.

These are my laptop's specs:
IBM Thinkpad R51
Pentium M 1.5ghz
512 DDR RAM
ATI Mobility Radeon 7500
Onboard Sound
Intel Wireless Adaptor (B/G)

That's all I can remember for the specs off the top of my head.

I'd appreciate any help. Thanks. :)[/QUOTE]
CTRL-ALT-F1

Log in to the text system with your username and password, then:

**sudo dpkg-reconfigure xserver-xorg**

and if you know exactly what you are doing, select the various options that your system is capable of handling, then when the process is completed:

**sudo reboot**

You can do a forum search for detailed instructions on changing screen resolution etc., but if it still doesn't work, repeat and select the "vesa" video driver.

---

