---
title: "A nice cpu temp &amp; fan monitoring program?"
date: 2011-02-03
forum: General Help
---

### Post by Xecutor13b on 2011-02-03
On XP I use speedfan which works nicely, but on Ubuntu, there is no version of speedfan, and it does not work in Wine. Are there any nice free programs out there for the Ubuntu OS that will monitor cpu temps and fan speeds?

Second question, is there a program to where I can create my own custom temperature max limits, and if it were to exceed, it would automatically shut the computer down? ( in case im out of the house, but the computer is still running). If I can get everything in one program, that'd be nice and If its something I have to pay for, im willing as long as the price is right. Does this even exsist?

---

### Post by dabl on 2011-02-03
The most popular Linux sensor monitoring package is lm-sensors, and of course hddtemp for hard drives.  But neither of these is a GUI display package, they only collect the sensor data for you.

Also, you need to be aware that lm-sensors is not able to detect every sensor in world, so your results are dependent on your hardware.

For desktop display, there are conky, gkrellm, and various widgets for KDE.  I'm not a Gnome user, but I do believe there are several display applets for Gnome.

For automatic shutdown, I'm not aware of a repo package that uses thermal data to trigger the shutdown (I've also never looked for one ...). I'm sure a smart script-writer could use cron and some logic to run a periodic check of the lm-sensors output, and execute a shutdown if a stated threshold is exceeded. However, modern CPUs all have a built-in thermal shutdown circuit, so I'm not sure an extra layer of shutdown capability would add any value.

I have used WinPower for UPS monitoring, to trigger a safe shutdown in a power loss situation.  You might want to consider that if you are leaving your system unattended for long periods of time.

---

### Post by marin123 on 2011-02-03
if youre using compiz in ubuntu, you can use screenlets for displaying sensor data. they act same way as gadgets in vista/7.

---

### Post by nilarimogard on 2011-02-03
Definitely Conky! Use Conky Colors for easy setting everything up.

---

### Post by cchhrriiss121212 on 2011-02-03
> Second question, is there a program to where I can create my own custom  temperature max limits, and if it were to exceed, it would automatically  shut the computer down?
Check your BIOS menu for this, most boards will have an auto shutdown limit even if you cannot alter it.

---

### Post by Frogs Hair on 2011-02-03
You can install senors-applet for the Gnome Panel after you install lm-sensors . The applet can display as a graph on your panel.

---

### Post by Xecutor13b on 2011-02-03
> **Frogs Hair said:**
> You can install senors-applet for the Gnome Panel after you install lm-sensors . The applet can display as a graph on your panel.

Thanks everyone for the info! I got everything installed and it works great, checked my bios, and labeled each temp accordingly.

Right now im trying to setup the alarm monitors in the sensors-applet, but I don't understand what "Scaling Parameters" "Sensor Value Multiplier" and "Sensor Value Offset" mean. Everything else is self explanitory.

What are "Scaling Parameters"?

---

