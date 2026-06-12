---
title: "Monitor CPU fan...???"
date: 2010-01-15
forum: General Help
---

### Post by robertcoulson on 2010-01-15
Hi
Is there a program within Ubuntu a or down loadable program that will monitor my CPU fan speed as the "Speedfan" I used in Windows XP...???
Bob

---

### Post by khelben1979 on 2010-01-15
You can install ksensors, it uses [lm_sensors]("http://en.wikipedia.org/wiki/Lm_sensors").

```
sudo apt-get install ksensors
```

---

### Post by robertcoulson on 2010-01-15
Installed Ksensor as you said...But, can't find it in any of the drop down menus...I am stupid..Eh
Bob

---

### Post by khelben1979 on 2010-01-15
Okay, in Debian the ksensors is placed in utilities, so you can try this in Ubuntu as well.

Other than this you just need to type ksensors. For instance I use alt + f2 in KDE, not sure about Gnome.

---

### Post by robertcoulson on 2010-01-15
I removed it and reinstalled it again, but I do not have a "utilities" menu that I can see...Well, thanks for trying to help...I appreciate it.
Bob

---

### Post by it_fixxer on 2010-01-15
(for gnome)
install K-sensors as above.
Open a terminal window and type
"sudo ksensors"
(Without quotes)
You should see a new icon appear on your panel beside the network icon.
right click on the new icon and select configure
From there you can select what you want but make sure you check the panel tab and the dock tab to make it viewable.
Hope this helps.

---

### Post by robertcoulson on 2010-01-15
That worked perfectly...Thanks soooooo much.
Bob

---

