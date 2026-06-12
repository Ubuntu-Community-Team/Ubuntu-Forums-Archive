---
title: "Nvidia Drivers, Compiz, Flash Lag"
date: 2009-10-08
forum: General Help
---

### Post by uv_goth on 2009-10-08
Wouldn't you know it but I get several problems at once!

Firstly I want to ask if it's worth installing Compiz on Kubuntu? Been going along happily without it for a while now but...

Flash lags badly. When I play online games, it severely lags when there's lots going on on-screen, which is, obviously, very annoying.

I've seen discussions about compiz affecting flash but I don't have it installed. I've tried in both Seamonkey and Firefox but both suffer the same problem.

I just installed the Nvidia Acceleration driver (180) but all that seems to have happened it my bottom panel is now transparent and no idea why!

---

### Post by NightwishFan on 2009-10-08
Does the panel still function? If not, then it may just need reset. You can also install an older or newer nvidia driver by following this thread:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by uv_goth on 2009-10-09
Panel still functions but is now mostly transparent. Not too big a problem.

The flash lag is getting very annoying and getting worse. Many solutions I've seen say compiz is a problem but I don't even have it installed.

---

### Post by NightwishFan on 2009-10-09
You can make sure compiz is disabled by setting desktop effects to none in the Appearance Properties.

About the panel, is it merely set to be transparent, or can you see nothing on it. There is a transparency setting in the panel properties.

Please tell me the model of your graphics card and version and desktop of Ubuntu.

---

### Post by beastrace91 on 2009-10-09
You might want to try adding the flash optimization listed [here](http://ubuntuforums.org/showthread.php?t=1193567)

Or in short run the following commands in terminal (in order): ```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

Basically it tells flash to enable GPU acceleration. But I would still recommend updating your driver to at least the 185 driver - the 180 is a bit dated at this point. (Personally I like to use the 190 beta driver)

~Jeff

---

### Post by uv_goth on 2009-10-09
Compiz isn't even installed according to Synaptic but have unchecked Enable Desktop Effects in Desktop settings.

The panel and KMenu transparency seems to be have solved. Looks like the visibility got switched off... :/

Using Kubuntu 9.04. Apparently it's a GeForce 7600 GS (I inherited it from my best friend so trusting what Nvidia X tells me)

------------
180 is the latest one shown in Hardware Drivers thus why I just installed it.

---

### Post by beastrace91 on 2009-10-10
If you want to try updating your gfx drivers you can always find the latest ones [here](ftp://download.nvidia.com/XFree86/)

To install them follow the instructions found [here](https://help.ubuntu.com/community/NvidiaManual)

~Jeff

---

