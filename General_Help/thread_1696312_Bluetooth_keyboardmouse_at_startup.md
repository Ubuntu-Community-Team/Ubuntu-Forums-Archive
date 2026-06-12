---
title: "Bluetooth keyboard/mouse at startup"
date: 2011-02-27
forum: General Help
---

### Post by dbrb2 on 2011-02-27
Hello,

I have a MS bluethooth keyboard/mouse, and a USB bluetooth dongle

In 10.1 I can add both with no problems - but I have to explicitly tell ubuntu to connect to the devices at each machine reboot, which means plugging in a wired mouse first :-)

Does anyone know how I can set the machine to connect automatically at every startup to both my keyboard and my mouse? I found a set of instructions here:

[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

But it is from 2007 and I'm not sure its still correct? 

Cheers,

Ben

---

### Post by Handssolow on 2011-03-03
I've just got my Microsoft Bluetooth mouse 5000 ver1.0 working on bootup. It may work for you.

[http://ubuntuforums.org/showthread.php?t=1699283](http://ubuntuforums.org/showthread.php?t=1699283)

---

### Post by bsntech on 2011-03-03
I have the Microsoft Bluetooth Elite Keyboard & Mouse setup.

When I installed it, I setup the keyboard and mouse just fine - but after a reboot, it wouldn't work.

So, I added this to my startup applications:

sleep 10
hcitool scan

I put that in a bash sh file then added it to the startup applications.  I do have to wait a good 10 seconds to load it - then after it is done, I have to start moving the mouse & hitting keys on the keyboard.  After a few seconds, they will engage.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com")

---

