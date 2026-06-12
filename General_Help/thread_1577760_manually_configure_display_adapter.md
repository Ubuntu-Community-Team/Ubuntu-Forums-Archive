---
title: "manually configure display adapter"
date: 2010-09-19
forum: General Help
---

### Post by stalkingwolf on 2010-09-19
In 8.04 i used this command to manually configure my graphics adapter.
sudo displayconfig-gtk

I would like to do the same thing in 9.10 and 10.04. How do i do it?
it is a unichrome pro in and older everex stepnote.

---

### Post by hrickh on 2010-09-19
In 10.04, it's located under System, Preferences, Monitors.

If you want to use the command line to launch, it's gnome-display-properties.

R.
==

---

### Post by stalkingwolf on 2010-09-20
with the adapter in the everex i have to reconfigure the adapter that doesnt give me the options

---

### Post by endotherm on 2010-09-20
a lot has changed since 8.04, so I'm not suprised that the old displayconfig doesn't work any more. in 8.10 I think, they upgraded X, and since, your config information is largely detected at boot (hence the xorg.conf is almost always blank now). you can always configure an xorg.conf if you want, but because it is no longer standard, most of the utilities that used to assist you in creating one are no longer part of the distro. you can view info about how your card was (or wasn't) autodetected in your xorg.log and xorg.0.log.

sorry I can't be of more help.

---

### Post by stalkingwolf on 2010-09-20
thanks ill try that

---

### Post by stalkingwolf on 2010-09-24
where do i find these documents?  I have tried sudo gedit and get blank documents.

---

### Post by endotherm on 2010-09-24
to which documents are you referring? 
the xorg.log?
just go to System -> Administrator -> Log file Viewer. 
the files themselves live in /var/log but use the log file viewer to access them.

---

### Post by stalkingwolf on 2010-09-25
thanks that worked , ill translate it and see if i can make it work.

---

