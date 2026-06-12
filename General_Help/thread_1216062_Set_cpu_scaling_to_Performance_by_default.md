---
title: "Set cpu scaling to Performance by default"
date: 2009-07-17
forum: General Help
---

### Post by L815 on 2009-07-17
Is there a way to set the gnome cpu scaling to use Performance on instead of Ondemand by default? Maybe in the gconf-editor settings?

---

### Post by tjsanda on 2009-11-08
sudo gedit /etc/init.d/ondemand

Change _ondemand_ to _performance_ in the lines:

start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
 
and:

echo -n ondemand > $CPUFREQ

---

### Post by tomaskob on 2009-11-23
it works good 4 me

and how can i set cpu scalling automaticaly to "ondemand" when im running battery? and when i put back ac power wanna it go back to "performance"

thanks

---

### Post by 1Michael1 on 2011-07-12
Can it damage a laptop in the long run to have it on Performance rather than a lower speed like "Ondemand" or "Powersave"?
My laptop runs a lot better with "Performance" rather than something else, but I don't want it to suddenly die or get overheated in a couple of weeks or months.

---

### Post by Trackieman on 2011-09-26
Worked for me too running 10.04
edit: (on a server setup with an AMD Athlon 64 Processor 3500+)

---

