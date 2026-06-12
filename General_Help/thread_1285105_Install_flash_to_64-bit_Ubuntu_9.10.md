---
title: "Install flash to 64-bit Ubuntu 9.10?"
date: 2009-10-07
forum: General Help
---

### Post by MrMatt on 2009-10-07
Okay.

basically, recently installed 9.10 beta,

and I cannot get Flash to install,

I have tried Ubuntu restricted extras, updating everything I can, numerous scripts, but I cant for the life of me get it to work!

or get it to get ia32-libs working :(

any suggestions?

---

### Post by khelben1979 on 2009-10-07
[Adobe Flash - Adobe.com]("http://get.adobe.com/flashplayer/?promoid=BUIGP").

[Here's a search result]("http://ubuntuforums.org/archive/index.php/t-295142.html") from Ubuntu.org which might help you out in this.

---

### Post by Sub101 on 2009-10-07
The best way to install that I know of is here:

[http://ubuntuforums.org/showpost.php?p=7717588&postcount=775](http://ubuntuforums.org/showpost.php?p=7717588&postcount=775)

```
#!/bin/bash
# Script created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

---

### Post by MrMatt on 2009-10-07
thank you sub101

that fixed it :)

---

