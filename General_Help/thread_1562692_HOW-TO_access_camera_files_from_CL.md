---
title: "HOW-TO access camera files from CL ?"
date: 2010-08-28
forum: General Help
---

### Post by zosky on 2010-08-28
hi yall. i hope im not being dense here :( some help plz...

picasa & digiKam can connect & grab pix/vids
+ i can see my files in dolphine with the path
*camera:/USB PTP Class Camera@usb:/*
**how do i get to these files from the command line ?**

i'd like to *process new videos* with a script
but for now i'm having to use the GUI to copy locally
... then run my script

my setup (though probably irrelevant): 
kubuntu lucid + a new shiny iphone4 
(preloaded with 4.0.2, so not JB'd, yet ;)
... otherwise i'd just SCP the files over)

any help would be appreciated

---

### Post by zosky on 2010-08-29
i figured it out (thanks to google)...
```
sudo apt-get install gphoto2
gphoto2 --get-all-files
```

---

