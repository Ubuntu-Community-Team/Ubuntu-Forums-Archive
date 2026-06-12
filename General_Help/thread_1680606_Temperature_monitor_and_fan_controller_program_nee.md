---
title: "Temperature monitor and fan controller program needed"
date: 2011-02-02
forum: General Help
---

### Post by rossh1992 on 2011-02-02
I installed ubuntu for the first time tonight and to put it simply everything is very confusing. I have been looking at different forums and everyone is installing programs in code and tbh i have no idea how to and i was wondering is there a program available that lets me monitor my CPU temp & alter fan speeds?

Thanks

---

### Post by takisan on 2011-02-02
I don't know about changing the fan speed, but there's a nice system monitor out there called Conky. I find configuring it to be a pain, so google Conky Config Script, and you should find a good one. For Monitoring Temperature, type $temp somewhere after TEXT in the file where you think it'd be a nice spot. $acpifan should give you your fan speed, but I know not how to change the fan speed. Check out [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) for more variables

---

### Post by rossh1992 on 2011-02-02
so im guessing that all controlled from script? is there no GUI program thats abit more simple to use?

Thanks

---

### Post by Noah0504 on 2011-02-02
> **rossh1992 said:**
> so im guessing that all controlled from script? is there no GUI program thats abit more simple to use?

Thanks
As far as I know, there isn't a GUI to the program.  I'm kind of surprised no one as come up with one.  You can also try out screenlets and maybe load a screenlet that will at least tell you your CPU temp.  There is also an applet (or whatever they're actually called) that can be added to the Gnome Panel to tell you your temp.  That can be found in Synaptic.

---

### Post by matt_symes on 2011-02-02
Hi

You can install GNOME Sensors Applet 2.2.3 to view the temperatures. Sits on a gnome panel. You might need to install lm-sensors as well for it to work. I cannot remember.

Also the CPU Frequency Scaling Monitor 2.30.0 applet is great for CPU scaling.

Not sure about the fan speed.

Kind regards

---

