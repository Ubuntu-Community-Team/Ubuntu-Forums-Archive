---
title: "Gnash Flash Player?"
date: 2009-12-09
forum: General Help
---

### Post by pluto4ps on 2009-12-09
Hi to all,

I am very happy to join Ubuntu World.

I want to install GNASH FLASH PLAYER, I want to ask all of you who ever tried it and how about the experience when compared to Adobe Flash Player.

I am currently using 64bit Ubuntu 9.10.

---

### Post by Leppie on 2009-12-09
For a 64bit system I would suggest installing adobe's 64bit version. You can download it [here]("http://labs.adobe.com/downloads/flashplayer10.html"). Extract the file.
Remove the default flash player:
```
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get remove flashplugin-installer
sudo apt-get remove --purge swfdec-mozilla
```

Copy the extracted file to one of the desstination dirs:
```
sudo cp /location/of/libflashplayer.so /usr/lib/adobe-flashplugin/libflashplayer.so
sudo cp /location/of/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
sudo cp /location/of/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

---

### Post by pluto4ps on 2009-12-09
So you would suggest not to go with GNASH FLASH PLAYER....

---

### Post by Hallvor on 2009-12-09
I think you should give it a go. It is open source.

---

### Post by Leppie on 2009-12-09
gnash seems to be pretty good for flv files, but I've had issues playing swf files (the interactive ones). Even adobe's linux version of flash is not as good as the windoze version. But they are the ones who determine flash behavior, so I guess it's better to stick with them. At least, for me that worked better.

---

