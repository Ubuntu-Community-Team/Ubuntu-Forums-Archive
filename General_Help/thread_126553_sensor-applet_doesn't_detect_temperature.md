---
title: "sensor-applet doesn't detect temperature"
date: 2006-02-06
forum: General Help
---

### Post by Lem0nHead on 2006-02-06
hello

I followed everything on [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) , but sensors doesn't detect the temperature... so sensor-applet doesn't too
in the other hand, /proc/acpi/thermal_zone/THRM/temperature has the temperature
any hints?

---

### Post by dcstar on 2006-02-06
[QUOTE=Lem0nHead]hello

I followed everything on [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) , but sensors doesn't detect the temperature... so sensor-applet doesn't too
in the other hand, /proc/acpi/thermal_zone/THRM/temperature has the temperature
any hints?[/QUOTE]
The only advice I can think of is to experiment with the lm-sensors.conf file, I had to make major tweaks to get all of my info in the right places.

The best thing would be to Google search with your motherboard type to try and find some information from another with the same hardware.

---

### Post by dudus on 2006-02-06
Same issue here. I played with the confs a couple of months ago, but I just quit trying. Maybe someone could clear this out a lil bit

---

### Post by nanotube on 2006-02-07
it all depends on your computer hardware... for example, i have a dell inspiron laptop, so instead of lm-sensors, i just loaded the i8k module to the kernel, and then the sensors-applet worked. just find whats right for your hardware...
also, hddtemp package can give you temp of your harddrives, and works with sensors-applet (in case you are interested).

---

### Post by Lem0nHead on 2006-02-07
I start to think it's a sensor-applet problem
I have hddtemp installed and "sudo hddtemp /dev/hda" returns the correct temperature
but sensors-applet just show a "hddtemp" item on the sensors, but keeps showing "No sensors enabled!" in the panel

---

### Post by nanotube on 2006-02-07
hi
well, did you enable the hdtemp sensor??
open up preferences for sensors applet, click sensors tab, you will see hddtemp item there. expand the item (click on the little triangle to the left of the hddtemp name), and there you will see your hard drive listed, with a label, and a checkbox. check the checkbox.

---

### Post by Lem0nHead on 2006-02-07
[QUOTE=nanotube]hi
well, did you enable the hdtemp sensor??
open up preferences for sensors applet, click sensors tab, you will see hddtemp item there. expand the item (click on the little triangle to the left of the hddtemp name), and there you will see your hard drive listed, with a label, and a checkbox. check the checkbox.[/QUOTE]

that's the problem
I can't expand the items :(
tried clicking the triangle, pressing ENTER... it just doesn't expand

---

### Post by nanotube on 2006-02-08
aha... i see... well, try restarting gnome-panel? (in terminal, type "killall gnome-panel"). or at worst, a restart of X, or even a reboot?

---

### Post by Lem0nHead on 2006-02-08
I tried rebooting and didn´t solve too :(

---

### Post by nanotube on 2006-02-10
well.. i guess at this point i am kinda out of ideas... try reinstalling the sensors-applet package?

---

