---
title: "flash/mozilla 3.5.4"
date: 2009-11-02
forum: General Help
---

### Post by badperson on 2009-11-02
HI,
I have an AMD opteron based machine...when I tried to install adobe flash on ubuntu 9.10, I got this message...
Error: Wrong architecture 'i386'

is there a version of flash I can download for my machine?
bp

---

### Post by Giblet5 on 2009-11-02
It sounds like you're running a 64-bit version.

If so, save this as "getflash" in your home directory: ```
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

Now, bring up a terminal window and enter ```
bash getflash
```

You owe me coffee now, in accordance with the prophecy.

---

### Post by badperson on 2009-11-02
heh-heh....that's worth a cup of coffee...thanks!
bp

---

### Post by danastasio on 2009-11-02
YES!! :D

Adobe is currently working on 64 bit flash for linux, it is still in alpha stage, but i can confirm that it works in an x86_64 environment with chromium.

here is a link:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by HiImTye on 2009-11-02
is there a way to get it working on a 32 bit version is the real question

flash is still buggy in FF - have to use seamonkey for flash still on alot of facebook apps

---

### Post by karimruan on 2009-11-02
I have a 64 bit machine running ubuntu 9.10 32 bit. I started with jaunty 32, and upgraded. To get flash working for me, I had to update to the newest firefox,(install all available updates too) and then remove all flash plugins i had, and run:

```


sudo apt-get install flashplugin-nonfree


```

It worked for me, don't know about it on 9.10, should work. But the flash support on 64 bit isn't great, which is why i run 32 bit Karmic.

---

### Post by danastasio on 2009-11-02
> **HiImTye said:**
> is there a way to get it working on a 32 bit version is the real question

flash is still buggy in FF - have to use seamonkey for flash still on alot of facebook apps

Are you sure you're using the latest flash version? I never had this problem when i was using a 32 bit system with FF. What exactly is buggy? what problems are you having?

---

### Post by HiImTye on 2009-11-02
> **danastasio said:**
> Are you sure you're using the latest flash version? I never had this problem when i was using a 32 bit system with FF. What exactly is buggy? what problems are you having?
youtube and such works fine but alot of faceboob apps (farm town, yoville, etc) work very buggily (it's a known issue, lots of google results about it and no fixes offered)

just do a quick google search of ubuntu flash yoville and you should see what I'm talking about

---

### Post by Uncle Spellbinder on 2009-11-02
Are you on 64 bit Karmic? Have Compiz (desktop effects) enabled? If so, disable desktop effects and all should be fine. There is a known issue with [Flash/64bit/Compiz](http://ubuntuforums.org/showpost.php?p=8220329&postcount=156).

---

### Post by HiImTye on 2009-11-02
32 bit has been this way since my first ubuntu install. also until recently I couldnt use desktop effects as I was using a coppermine (as my computer was still in calgary)

---

