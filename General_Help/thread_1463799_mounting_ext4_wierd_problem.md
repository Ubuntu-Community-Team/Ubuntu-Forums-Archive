---
title: "mounting ext4 wierd problem"
date: 2010-04-27
forum: General Help
---

### Post by cmcanulty on 2010-04-27
OK I finally dumped my XP entirely from my netbook and left only Ubuntu 9.10. First the install from a flash drive is really flaky. It took 3 installs before there were major boot hassles. Then when I went to copy my 70GB of Home files from my ext HD it wouldn't find it., the ext HD is using the ext4 file system.Also it won't recognize my other 1 GB flash drive. Here is the wierd thing though. Both work fine if I boot using the USB live install flash drive and that is how I managed to copy all my files. So there is some USB type driver on the live 9.10 install that isn't installed with the system. When I was dual booting on the netbook Ubuntu recognized both of them easily. Now I don't want to constantly have to go with the live install as it is very slow. I need to figure out what is missing and causing this and I have no clue where to even start, thanks all.

---

### Post by dino99 on 2010-04-27
ok so goto synaptic and search for usb, you might install usbmount and usbutils, then install mountmanager and tweak the settings as you want/need

note: as always logs can teach you about troubles

---

### Post by Martje_001 on 2010-04-27
Check /var/log for any clues.

---

### Post by cmcanulty on 2010-04-27
there are several folders and files in/var/log where do I start?

---

### Post by dino99 on 2010-04-27
> **cmcanulty said:**
> there are several folders and files in/var/log where do I start?

gnome-panel: system - admin - log viewer

---

### Post by cmcanulty on 2010-04-27
OK sorry I have never used or even looked at that tool before. But the last thying alphabetically is usr no var

---

### Post by dino99 on 2010-04-27
> **cmcanulty said:**
> OK sorry I have never used or even looked at that tool before. But the last thying alphabetically is usr no var

you just dont see the full path but only the files in it.

note: your distro is like your car or your wife, you have to look at her  :oops:

---

### Post by cmcanulty on 2010-04-27
OK but there are hundreds of files in there what am I looking for?

---

### Post by dino99 on 2010-04-27
> **cmcanulty said:**
> OK but there are hundreds of files in there what am I looking for?

are you really there : system - admin - log viewer ?

there is no so much files :confused:

on the left pane, click on the sign at the beginning of auth.log / daemon.log / messages / syslog / user.log  line and choose the latest date in there.

---

### Post by cmcanulty on 2010-04-27
I have the sys log but it won't let me send as it is too long everything was from yesterday and today as I installed it yesterday. Is there a way to send a long file without getting in trouble with the forum? It is 470KB as I made it into a pdf

---

