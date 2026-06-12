---
title: "NVIDIA setting is not working after upgrade"
date: 2011-06-14
forum: General Help
---

### Post by aab001 on 2011-06-14
after I have  upgraded my ubuntu 10.10 to 11.04 I lost my taps menu ( application,  places and sytem). I have reboot with the recovery mode which is working  with low graphic and works fine. when i go to nvidia setting i get the  message [I]You do not appear to be using the NVIDIA X driver. Please  edit your X  configuration file (just run `nvidia-xconfig` as root), and  restart the  X server.
i don't know what to do?
please I need your help.[/I]

---

### Post by pqwoerituytrueiwoq on 2011-06-14
open terminal 
sudo nvidia-xconfig
sudo service gdm restart

---

### Post by seawolf167 on 2011-06-14
If needed (in case you get errors running in a graphics mode) you can also run the commands posted by aab001 through tty1 by hitting [CTRL][ALT][F1] then typing the commands

---

### Post by aab001 on 2011-06-14
I have tried all the commands but still it is not working

---

### Post by seawolf167 on 2011-06-14
> **aab001 said:**
> I have tried all the commands but still it is not working

Any error messages? Any new warning messages? What exact commands did you type? Was there any output at all?

---

### Post by aab001 on 2011-06-14
> **seawolf167 said:**
> Any error messages? Any new warning messages? What exact commands did you type? Was there any output at all?
these are the commands 
sudo nvidia-xconfig
sudo service gdm restart
and  there are no errors but still the same situation is there

---

### Post by aab001 on 2011-06-14
is there any suggestions!!

---

### Post by aab001 on 2011-06-17
since no one helping me in my problem who can I go back to 10.10 without losing my software and documents

---

### Post by LowSky on 2011-06-17
> **aab001 said:**
> since no one helping me in my problem who can I go back to 10.10 without losing my software and documents

uninstall the latest driver from addtional drivers app.

then reinstall then reboot...

and you can't go back without fresh install

---

### Post by aab001 on 2011-06-18
> **LowSky said:**
> uninstall the latest driver from addtional drivers app.

then reinstall then reboot...

and you can't go back without fresh install

I tried to uninstall and install again but nothing change. 
under that driver it says the diver is activated but not currently in used. now i just use the recovery mode to work in my pc.:confused::confused::confused::confused: I don't really now what to do.

---

### Post by aab001 on 2011-06-23
still i did not solve the problem.

---

