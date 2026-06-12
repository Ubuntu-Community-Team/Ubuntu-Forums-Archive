---
title: "buggy 64-bit flash on unity?"
date: 2011-05-08
forum: General Help
---

### Post by princeofnam on 2011-05-08
I've always had buggy flash on 64bit 10.04 but since upgrading to 11.04 things have grown worse.  Blotches of unclickable area will appear and full-screen is completely inaccessible.  Anyone suffering from the same symptoms? Solutions?

---

### Post by garvinrick4 on 2011-05-09
I use this and it works for me it is the beta Native 64 bit.
[http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)
If you need to know how to install just holler.

---

### Post by garvinrick4 on 2011-05-09
##Here is way to remove old flash and install from tarball. First six sudo commands are just to remove old flash and leftovers.
  sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper  
 sudo rm -f /usr/lib/mozilla/plugins/*flash*  
 sudo rm -f ~/.mozilla/plugins/*flash*  
 sudo rm -f /usr/lib/firefox/plugins/*flash*  
 sudo rm -f /usr/lib/firefox-addons/plugins/*flash*  
 sudo rm -rfd /usr/lib/nspluginwrapper  
 ##Download Flashplayer 64 bit Native square to [COLOR=Red]Desktop[/COLOR]:
 [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
 rick@rick-HP:~$ cd Desktop  
 rick@rick-HP:~/Desktop$ ls  
 flashplayer10_2_p3_64bit_linux_111710.tar.gz 
 rick@rick-HP:~/Desktop$ sudo tar zxvf flashplayer10_2_p3_64bit_linux_111710.tar.gz  
 [sudo] password for rick:  
 libflashplayer.so  
 rick@rick-HP:~/Desktop$ sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
 rick@rick-HP:~/Desktop$ sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
 
#Done:

---

### Post by princeofnam on 2011-05-09
hmm.  i followed your instructions but I still have the same errors?

---

### Post by garvinrick4 on 2011-05-09
Make sure firefox is not running when you give commands.
```
sudo killall -9 firefox
```

---

### Post by akand074 on 2011-05-09
Install LovingLinux's[ flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on for firefox. It'll wipe every flash you have on your system and install the correct and most up to date one for your system automatically.

---

### Post by garvinrick4 on 2011-05-09
> **akand074 said:**
> Install LovingLinux's[ flash-aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") add-on for firefox. It'll wipe every flash you have on your system and install the correct and most up to date one for your system automatically. It does install the same 64 bit beta as in post 3 unless you choose expert mode and change to another for 64 bit system. Works very well for those that choose to
use extensions and in expert mode can modify the script with a GUI very easily. I myself choose to maintain my own with as few modifications as I can and directly from Adobe.com but every user has his or her own preferences.

---

