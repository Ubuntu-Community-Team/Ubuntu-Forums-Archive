---
title: "disk usage analyzer going funky?"
date: 2009-07-02
forum: General Help
---

### Post by cirabisi2009 on 2009-07-02
ok. so i have ubuntu installed on 2 of my laptops. 

my toshiba satellite a305-s6858 dual booting linux ubuntu and vista
and
acer aspire one AOA 150 zg5 dual booting ubuntu and xp home


ok now my problem. when i go into the ubuntu on my toshiba and click on disk usage analyzer it tells me that i have 604gb hd and i have used 340gb. on my acer it says i have 240gb and have used over 160gb. the toshiba spec sheet says it has a 320gb hard drive and my acer has a 120gb hard drive. 

i guess my real question is. Does Windows really take that much space?

---

### Post by drs305 on 2009-07-02
DUA can be a bit confusing in the way it presents things. I don't know what you are looking at specifically, but remember that if you have extra devices mounted on your system they are generally included in the reported sizes. You can go into the Edit > Preferences section and amend exactly what you want DUA to look at. 

I have a bit more explanation on using DUA in my guide on Disk Space, linked to in my signature line.

---

### Post by cirabisi2009 on 2009-07-02
here is what i see

---

### Post by drs305 on 2009-07-02
cirabisi2009,

Since you have / selected, anything mounted anywhere on / will also be included. For example, if you have a 100GB external hard drive mounted on /media/myexternal, that 100 GB will be included in the total reported by DUA.  You will get a better idea of what is on your system if you expand DUA into a tree view.

For looking at the system partition, if I want an accurate picture with DUA, I normally close out all my other apps, then run "sudo umount -a". That generally unmounts all non-system partitions and gives me a better picture of what is actually on the system partition. 

Looking at the attachments, it shows you are using 60GB in /boot, which is pretty unusual to put it mildly. If you don't know why you have 60GB of stuff in /boot, I'd again recommend going to the "Disk space" link in my signature line to see what is occupying the space. There are also terminal commands that may give you a better idea of what is on your system.

Older versions of DUA also included the .gvfs information, which generally *doubled* the actual space since it reported the 'virtual' information provided by gvfs. If you have an older version of DUA there will be a section where you can untick your home's .gvfs folder to better report physical disk usage.

---

