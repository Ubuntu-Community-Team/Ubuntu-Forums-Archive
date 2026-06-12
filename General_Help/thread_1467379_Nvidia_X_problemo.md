---
title: "Nvidia X problemo"
date: 2010-04-30
forum: General Help
---

### Post by bluestar14 on 2010-04-30
every time i boot, it says "ubuntu is running in low-graphics-mode......" and i click "restart x"..and i can't enable desktop effects, i reinstalled nvidia driver, but it still doesn't work and same thing happens

---

### Post by rnerwein on 2010-04-30
hi
i have a Geforce 9300 GE and GeForce 9200 on my box and had much "fun" with the nvidia driver in Karmic Koala.
but still i am running lucid lynx ( since beta 2 ) the graphic runs like a charme. ( running koala too ).
do an upgrade to lynx there are the nvidia driver are included in the system.
ciao

---

### Post by bluestar14 on 2010-04-30
also can't play super tux cart(but i could 3 reboots ago!)


whoops srry, forgot to mention: i am running lucid lynx final

---

### Post by bluestar14 on 2010-04-30
Plz!!!!

---

### Post by bluestar14 on 2010-04-30
anybody?

---

### Post by bluestar14 on 2010-04-30
i need my tux!!!

---

### Post by rnerwein on 2010-05-01
> **bluestar14 said:**
> every time i boot, it says "ubuntu is running in low-graphics-mode......" and i click "restart x"..and i can't enable desktop effects, i reinstalled nvidia driver, but it still doesn't work and same thing happens

good morning
please tell some of your secrets:
first: which nvidia bord you have ?
second: are you using the ubuntu nvidia driver ?
third: which driver version are you using ?

this will help us something a little more ( hope so ).

ciao

---

### Post by peterpan7191 on 2010-05-01
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)


hope this would help... :)

---

### Post by bluestar14 on 2010-05-01
well..ok, i did a reinstall and it was fine rebooting until i installed burg, maybe that has something to do with it?

and here are my "secrets"(repectively)
1:Nvidia Geforce MX 100/200
2:yes
3: i think nvidia-96


still have to try that link.....

---

### Post by bluestar14 on 2010-05-01
and the link didn't work....

---

### Post by bluestar14 on 2010-05-01
well, i uninstalled burg, and all is fine, expect plymouth screen is still low-res and instead of logo, text shows, but i still want my burg and my plymouth!

---

### Post by bluestar14 on 2010-05-01
well, now plymouth is working, so now its a matter of installing burg without it affecting nvidia driver.....

---

### Post by strange_cathect on 2010-05-01
I had this problem and was able to resolve it.

First, go to synaptic and download a package called nvidia-settings.

Then, go to System\Administration\Hardware Drivers.

Select the version that is recommended. (You may have to download it).

Then, click activate.

Afterward, you will have to reboot. Make sure to do a true reboot and not just logging out. 

After reboot, you should be able to change your monitor settings using nvidia-settings.

---

### Post by bluestar14 on 2010-05-01
ok, i uninstalled nvidia driver, did what you said, installed burg, still have same problem, now uninstalling burg

---

