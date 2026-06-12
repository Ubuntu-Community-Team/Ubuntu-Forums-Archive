---
title: "Terminal and Install"
date: 2010-12-20
forum: General Help
---

### Post by David52 on 2010-12-20
I am seeking help again. I have a Win TV 1250 tv turner card I am trying to get working.  I have a few other post out on this one. When I go into the terminal under lspci, it does show the card.

04:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04

 I did install tv time viewer but I have no luck so far. I was turned onto a link

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification)

and yes I did download the firmware they speak of to my desktop. It is in a zip format. I have not extracted the file yet.
now per this post
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification)
I do not know how to place that into the lib/firmware folder. I know where the folder is, but I cannot drag it and I believe to get it in there proper I should use the terminal to install it. Hope someone can help me on this. 
david

---

### Post by lovinglinux on 2010-12-20
> **David52 said:**
> I am seeking help again. I have a Win TV 1250 tv turner card I am trying to get working.  I have a few other post out on this one. When I go into the terminal under lspci, it does show the card.

04:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 04

 I did install tv time viewer but I have no luck so far. I was turned onto a link

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification)

and yes I did download the firmware they speak of to my desktop. It is in a zip format. I have not extracted the file yet.
now per this post
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1200#Identification)
I do not know how to place that into the lib/firmware folder. I know where the folder is, but I cannot drag it and I believe to get it in there proper I should use the terminal to install it. Hope someone can help me on this. 
david

Just run the commands suggested there to extract and move the files. To copy anything to lib/firmware you need to use sudo.

```
wget http://steventoth.net/linux/hvr1200/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://steventoth.net/linux/hvr1200/extract.sh
/bin/sh extract.sh
sudo cp v4l-cx23885-enc.fw v4l-cx23885-avcore-01.fw dvb-fe-tda10048-1.0.fw /lib/firmware
```

---

