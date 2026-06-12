---
title: "bluetooth-applet off at startup"
date: 2010-11-21
forum: General Help
---

### Post by Trixilver on 2010-11-21
Hi. I was wondering if there is a command I can simply add to the end of bluetooth-applet to disable it as soon as it runs? Something like:

```
bluetooth-applet -off
```

I want to add this to my Startup Applications so that by default, bluetooth is turned off when the computer is restarted.

---

### Post by papibe on 2010-11-21
The applet appears because it is run on the Start Up Applications. The best way to disable it is System -> Preferences -> Start Up Applications. There, uncheck the Bluetooth Manager.

Good Luck!

---

### Post by Trixilver on 2010-11-21
But I still want the applet to start, I just don't want bluetooth to be enabled. i.e. when you left click on the applet you can turn bluetooth off. My question is: how do I get the applet to start with bluetooth **already** turned off.

---

### Post by Trixilver on 2010-11-21
bump

---

### Post by papibe on 2010-11-22
I see. Unfortunately bluetooth-applet, bluetooth-properties and bluetooth-wizard do not receive options.

I'm not sure if this will work but you can use hciconfig:
```
$ man hciconfig
```
I believe you close all devices by doing:
```
$ hciconfig -a down
```
I have NOT try this in my computer, please **read the man before** trying.

I hope it helps.

---

### Post by boom08 on 2010-11-26
How do I keep bluetooth from turning on in the first place?
When it shuts down, i keeps saying "* Stopping bluetooth" and it won't shutdown. Why does it do this?

---

### Post by giowck on 2010-11-26
in order to disable completely bluetooth you should add to /etc/rc.local

this line:

```
rfkill block bluetooth
```

If you need to activate bluetooth you can just use as usually the blueooth applet!

---

### Post by corruptor1972 on 2011-02-13
[This works for me]("http://ubuntuforums.org/showpost.php?p=10455811&postcount=6")

---

