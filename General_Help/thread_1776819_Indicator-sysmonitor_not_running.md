---
title: "Indicator-sysmonitor not running"
date: 2011-06-06
forum: General Help
---

### Post by holadebob on 2011-06-06
I've installed Indicator-sysmonitor panel applet 3 times, looked in Add to Panel, Accesories, System Tools, Googled it, can't get it to show up.

I've got other applets on the panel, like network monitor, etc.

Anyone got a clue what I am not doing?

---

### Post by linuxinstalledfromhdd on 2011-06-06
Did you install the extra packages in Synaptic package manger for that?

---

### Post by holadebob on 2011-06-06
Which files? Library files for applets, and some other indicator files like session, applet-session and messages..

thanks for the quick response


Edit: I jumped over myself to answer quickly forgot to say I have those files installed..

---

### Post by holadebob on 2011-06-06
Looking for possible other packages to install I found that I needed python-psutil but it's already installed.

---

### Post by Frogs Hair on 2011-06-06
Have you installed lm-sensors ? I think the the hardware monitor for the panel requires them.```
sudo apt-get install lm-sensors
```

---

### Post by holadebob on 2011-06-06
Just reinstalled lm-sensors, no updates, no reinstallation cause it exists. Also I read where hdd temp is needed , which I reinstalled also. It's kinda strange - I've looked in the Menu set up and it's not there, and accesories of course, and it's not there.

I haven't a clue. Normally, everything I do to this 10.04 works smoothly - this is the first problem I've had with it for quite a while.

---

### Post by collisionystm on 2011-06-06
> **holadebob said:**
> I've installed Indicator-sysmonitor panel applet 3 times, looked in Add to Panel, Accesories, System Tools, Googled it, can't get it to show up.

I've got other applets on the panel, like network monitor, etc.

Anyone got a clue what I am not doing?


Yup... you are trying to start it wrong!!!

you need to ALT+F2

type 

inidicator-sysmonitor

ENTER

Make sure you add it to your startup applications if you enjoy it, that way you dont have to do this everytime.

---

### Post by collisionystm on 2011-06-06
I know this because I installed it on my 11.04 lol. It has to be manually ran, with gnome or unity.

---

### Post by holadebob on 2011-06-06
Terrible response here -no go. It doesn't give me any errors and acts as if it runs fine, but no display, no entry in accesories, nada.

---

### Post by collisionystm on 2011-06-06
Run it in terminal and post output

---

### Post by holadebob on 2011-06-07
clark@clark-office:~$ indicator-sysmonitor
Traceback (most recent call last):
  File "/usr/bin/indicator-sysmonitor", line 476, in <module>
    sys.exit(main(sys.argv))
  File "/usr/bin/indicator-sysmonitor", line 468, in main
    i = IndicatorSysmonitor()
  File "/usr/bin/indicator-sysmonitor", line 371, in __init__
    self.ind.set_label("Init...")
AttributeError: 'appindicator.Indicator' object has no attribute 'set_label'
clark@clark-office:~$ 


sorry for the delay, was sleeping :)

---

### Post by holadebob on 2011-06-07
Collisionystm,

[https://bugs.launchpad.net/indicator-sysmonitor/+bug/743712](https://bugs.launchpad.net/indicator-sysmonitor/+bug/743712)    with the response:

 "The appindicator lib shipped in lucid does not provide the API needed by sysmonitor to work (setting a label next to the icon).

Unfortunately, this bug won't fix.

Changed in indicator-sysmonitor:
status:	 New &#8594; Won't Fix
summary:	 - Fail to start, maybe missing phyton depends?
+ [lucid] Fail to start, maybe missing phyton depends?"

Does that mean this is a dead end, if you have any ideas please let me know. I think this is the only panel applet out there that is supposed to work with 10.04, from the Ubuntu depository.

---

