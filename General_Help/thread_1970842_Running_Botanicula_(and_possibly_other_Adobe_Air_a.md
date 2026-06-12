---
title: "Running Botanicula (and possibly other Adobe Air application) in Ubuntu 12.04 AMD64"
date: 2012-05-01
forum: General Help
---

### Post by Emblem Parade on 2012-05-01
This method does not fully install Air on your system. Instead, it just "adds Air" to your game/application in order to make sure it works. Good if you don't want to infect your system with Air.

Make sure you start in the directory in which you have "Botanicula.air", and then run this:

```
mkdir Botanicula Botanicula/air Botanicula/app ~/BotaniculaSaves
wget http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRSDK.tbz2
tar xvjf AdobeAIRSDK.tbz2 -C Botanicula/air
unzip -d Botanicula/app Botanicula.air
sudo apt-get install libnss3-1d:i386 libgtk2.0-0:i386 libasound2-plugins:i386 libcanberra-gtk-module:i386
echo '100,off,high,en,1,0' > ~/BotaniculaSaves/settings.txt
echo 'cd $(dirname "%0") && ./air/bin/adl -nodebug app/META-INF/AIR/application.xml app/' > Botanicula/botanicula
chmod +x Botanicula/botanicula
```

To run, doubleclick on "botanicula" inside the Botanicula directory.

---

### Post by salatt on 2012-12-09
Thanks

---

