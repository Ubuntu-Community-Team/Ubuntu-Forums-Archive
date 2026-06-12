---
title: "Fullscreen flash problem"
date: 2009-11-03
forum: General Help
---

### Post by Zael Faroe on 2009-11-03
I am running Kubuntu 9.04 with the proprietary graphics drivers installed for a nVidia GTS 250 with dual 19" monitors in a TwinView setup. Anytime I try to fullscreen a flash video, the flash goes into fullscreen mode, but instead of the video being full screen, the video is still the same size and the rest of the monitor is black (excluding the buttons). I have this problem with and without desktop effects enabled.

Does anybody know the cause of this and how to fix it? I tried to list everything I felt was relevant, but I would be happy to provide any additional information.

Thanks.

P.S. It is an x64 install.

---

### Post by Zael Faroe on 2009-11-06
Bump.

Anyone?

---

### Post by Giblet5 on 2009-11-06
Are you using the x64 flash beta or the one from the repository?

This script will remove 32-bit flash and install the x64 beta.

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

---

### Post by Zael Faroe on 2009-11-06
The one from the repository.

---

### Post by Giblet5 on 2009-11-06
Save that script and run it.

---

### Post by Zael Faroe on 2009-11-06
After running the script, full screen still just blacks out the rest of the screen and keeps the video the same size.

---

### Post by P4man on 2009-11-06
I have the same with most flash movies (also using dual monitor, but nvidia)
I figured it was due to the fact my monitors have different resolutions, but now that you mention it, the size doesnt reflect the other monitor's either.

Further more it insists on going fullscreen on the wrong monitor.

I have this on youtube, but not on some other websites that incorporate youtube clips with different players. Some work fine (though still only on the "wrong" monitor)

 Let me find an example.

---

### Post by Giblet5 on 2009-11-06
Firefox, or Chrome?


Maybe it only works here because I'm running separate screens...

Well, at least you have the 64-bit flash now. You would have had unrelated trouble otherwise.

---

### Post by Zael Faroe on 2009-11-06
I always get them on the right monitor. I haven't tried every video site out there, but so far I haven't been able to get any flash videos to go full size.

---

### Post by Zael Faroe on 2009-11-06
I use chromium mostly, but after running the script ran the video in firefox because flash stopped loading in chrome (probably because of the shortcut thingy)

---

### Post by P4man on 2009-11-06
Cant find an example that works. My fav news site just switched to the default youtube player and no longer works full screen :(

Not really a work around, but well, minitube works full screen:
[http://www.getdeb.net/app/Minitube](http://www.getdeb.net/app/Minitube)

Does require installing phonon:

sudo apt-get install phonon-backend-gstreamer

great little app but I would also like a better solution. But I fear its a flash bug that will not get high priority from adobe.

FWIW I use 32 bit ubuntu.

---

### Post by Giblet5 on 2009-11-06
I switched to Twinview and get the same thing. Ouch.

I agree that this is an Adobe issue that will see very little attention.

Linux: strike 1
x64: strike 2
Twinview: strike 3

(even if it does the same thing on 32-bit, it's Adobe...)

(GTX 280, x64)

---

### Post by P4man on 2009-11-13
If you try this flash movie:
[http://therealnews.com/t/index.php?option=com_content&task=view&id=31&Itemid=74&jumival=4462](http://therealnews.com/t/index.php?option=com_content&task=view&id=31&Itemid=74&jumival=4462)

(and any other using that same player) it does work fine in full screen, even with twinview. Im wondering if its something in the HTML ?

---

