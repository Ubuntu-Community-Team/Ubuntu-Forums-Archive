---
title: "How to add items to panel in 11.10"
date: 2012-01-05
forum: General Help
---

### Post by meetdilip on 2012-01-05
I have installed netspeed but unable to add it to task manager or any other place where I can see the meter. Any way out ? Thanks.

---

### Post by Frogs Hair on 2012-01-05
I just tested this and it works . Start it from dash once installed . 
[http://shuffleos.com/561/indicator-multiload-system-info/](http://shuffleos.com/561/indicator-multiload-system-info/)

---

### Post by meetdilip on 2012-01-05
Thanks. 

It shows other reading correctly but network shows down 0 bytes /sec, up 0 bytes / sec even when the system monitor shows the reading. I use a CDMA based USB modem for internet. Please find the screen shots attached.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210296&stc=1&d=1325782412[/IMG]


Also any method to check the total usage for a particular period ?

---

### Post by Frogs Hair on 2012-01-05
There may be something useful at the link and if not it's good resource anyway . [http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by meetdilip on 2012-01-05
Thanks.

---

### Post by imachavel on 2012-01-05
> **Frogs Hair said:**
> I just tested this and it works . Start it from dash once installed . 
[http://shuffleos.com/561/indicator-multiload-system-info/](http://shuffleos.com/561/indicator-multiload-system-info/)

sudo add-apt-repository ppa:indicator-multiload/stable-daily
sudo apt-get update
sudo apt-get install indicator-multiload

? I tried it in mine, didn't work. BEEECAUSE, it was already installed from the repository. I just searched it and opened it. Nice link :popcorn:

---

### Post by imachavel on 2012-01-05
> **meetdilip said:**
> Thanks. 

It shows other reading correctly but network shows down 0 bytes /sec, up 0 bytes / sec even when the system monitor shows the reading. I use a CDMA based USB modem for internet. Please find the screen shots attached.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210296&stc=1&d=1325782412[/IMG]


Also any method to check the total usage for a particular period ?

good question mine works fine

---

### Post by meetdilip on 2012-01-05
It is an USB modem. Ubuntu detected it automatically and I am able to browse without any issues. Any work out ?

PS : I restarted twice.

---

