---
title: "Premotedroid - Android remote control bluetooth problem"
date: 2010-09-14
forum: General Help
---

### Post by r00cky on 2010-09-14
Hello!

I want to control my Ubuntu laptop with Android phone. I choose Premotedroid remote control software: 
[http://code.google.com/p/premotedroid/](http://code.google.com/p/premotedroid/)
[http://www.remotedroid.net/](http://www.remotedroid.net/)

It requires Java SE Runtime Environment 1.5 or higher, which I have.

I have a problem starting Bluetooth server on ubuntu 10.04. Program starts correctly, an icon pops up in the panel.. only BT server is not running. The BT module is on, as well I can transfer files via BT (so BT itself works fine).

Does anyone have an idea what to do?

Thanks!

---

### Post by phuturism on 2010-09-19
Doesn't remotedroid function over wireless networks, not bluetooth?

---

### Post by rosencrantz on 2011-02-01
It's two different apps: Remotedroid is WiFi only, Premotedroid should also support bluetooth.
To get the bluetooth server running, you have to add the bluecove modules packed with the PRemoteDroid executable to your Java classpath:
export CLASSPATH=$CLASSPATH:<path to jar>/bluecove-2.1.0.jar:<path to jar>/bluecove-gpl-2.1.0.jar
java -jar PRemoteDroid-Server.jar
After pairing my phone, setting a password and adding the connection in the client, everything worked without a hitch.
Cheers,
rosencrantz

---

### Post by d.tamm on 2011-02-24
I had to install libbluetooth-dev to get the Bluetooth server running on my Ubuntu 10.10 64bit.
At another place I saw that you may have to replace the bluecove files with 64 bit versions, but I never tried that.

---

