---
title: "Accessing sensor information"
date: 2010-06-02
forum: General Help
---

### Post by Gonz_91 on 2010-06-02
Hello everyone!

I own a Toshiba Satellite laptop, which I sometimes use in bed, usually to wrap up something before going to sleep.
In those conditions, it sometimes overheats and shuts down.
I figured it'd have to have a thermometer somewhere which told it when it was time to cut the power, and using Hardinfo, I can check said thermometer.
However, I'd like to know more, so my question is as follows: does anyone know about a simple program that displays this information, namely a panel applet?
If not, maybe a command line utility?

Thanks a lot in advance!

---

### Post by cryptotheslow on 2010-06-02
Depending on your version of Ubuntu here but try:

Right-Click on the panel, Select Add To Panel, from the list select "Hardware Sensors Monitor".

Once it is on the panel you can right-click it and choose Preference to configure which sensors to display.

---

### Post by utnubuuser on 2010-06-02
The sensors applet can be installed with > sudo apt-get install sensors-appletthen follow the above instructions.

---

### Post by fooman on 2010-06-02
may have to install the applet first.....open a terminal and type or copy/paste:
```
sudo apt-get install lm-sensors sensors-applet
```then in the terminal,  run:

```
sensors-detect
```answer the questions accordingly.  when complete,  you could run in a terminal:

```
sensors
```or, for a graphical view,  right-click on the top or bottom panel and choose "add to panel"

scroll through the list for "sensors applet" or "hardware sensors monitor", select it and click "add"

hope that helps.

---

### Post by Gonz_91 on 2010-06-02
> **cryptotheslow said:**
> Depending on your version of Ubuntu here but try:

Right-Click on the panel, Select Add To Panel, from the list select "Hardware Sensors Monitor".

Once it is on the panel you can right-click it and choose Preference to configure which sensors to display.

This plus
```
sudo apt-get install sensors-apple
```

Is just what I was looking for!

Thanks a lot, everyone, marking solved...
:D

---

### Post by dino99 on 2010-06-02
sensors-detect might duplicate the already built-in modules in kernel, so dont use it

you might check into synaptic that fancontrol and the "tosh"* packages are installed

---

