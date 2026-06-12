---
title: "Flash: 32-bit vs. 64-bit"
date: 2009-11-19
forum: General Help
---

### Post by herbertportillo on 2009-11-19
I run Karmic 64-bit on my computer, but I run 32-bit Flash plugin with the nspluginwrapper. Since I did the clean install of Karmic when it came out a few weeks ago, Flash has been working strangely. When I'm on a webpage with Flash, clicking sometimes does nothing. The only workaround is to disable all desktop effects in Appearance Preferences.

So, a few days ago I installed the alpha 64-bit Flash plugin from Adobe, and it seemed to fix that problem, but the plugin makes Firefox crash on any Flash website. But since I use the dev build of Google Chrome as my default browser, it can handle the plugin. The only annoying thing that happens is that Chrome always says libflashplayer.so crashed the browser, but it remains open and I can continue browsing webpages with Flash, so it doesn't really crash the browser. It just says it does. Hmm.

If you've read this far, I appreciate it, but there's more :)

I also noticed that 64-bit Flash was way choppier in fullscreen, and 32-bit Flash with nspluginwrapper is waaay smoother so I deleted 64-bit Flash and re-ran flashplugin-installer. But I have to stick to no cool desktop effects to have a Flash that works all the time.

Has anyone encountered this as well? Any and all input is appreciated. Thx.

---

### Post by Giblet5 on 2009-11-19
Create a file called x64flash in your home directory by opening a terminal window (Applications -> Accessories -> Terminal) and entering: ```
gedit x64flash
```

Select, copy, and paste the following to the gedit window: ```
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

Save it and exit gedit.

In the terminal window enter: ```
bash x64flash
```

When prompted for your password enter it (it won't echo anything) and hit Enter.

You owe me coffee now. It is the law.

---

### Post by herbertportillo on 2009-11-19
Does that script make the 64-bit Flash plugin run smoother than just downloading the plugin and moving it to ~/.mozilla?

Oh, I don't drink coffee. It's bitter and gross. Haha, I prefer a tall cool glass of Orenthal James in the morning.

---

### Post by Giblet5 on 2009-11-19
The script completely fixes the flash problem for the system, not just for your account.

Re coffee: it is only bitter if it's done wrong, and the LAW is on my side. THE LAW. ;)

---

### Post by herbertportillo on 2009-11-19
Sorry, but it made it worse. Now I can't see any Flash content at all.

---

### Post by herbertportillo on 2009-11-19
Hah! I forgot to restart the browser. Oops. Forgive me for my idiocy.

Thanks for the script. It works perfectly now. But I am still disinclined to buy you coffee. After all, OJ can get away with the law, until he breaks into someone's hotel room with a gun. :P

Just curious, is it a 32-bit or 64-bit Flash now? It re-installed nspluginwrapper, so I'm assuming 32-bit which isn't a big deal.

Edit: Awww, it's still choppier in fullscreen. Oh well. At least I get my fancy schmancy desktop effects. :)

---

### Post by Giblet5 on 2009-11-20
That's the 64-bit Flash 10 beta.

No idea why it's still only beta - it works quite well.

As for choppiness, check to see if you're using the Xinerama extension on Xorg: ```
xdpyinfo | grep -i xinerama
```

No output = no-you're-not

That extension can cause problems or miracles. If it's not on, see if you can install a hardware driver for your graphics card. If it is on, try disabling it via the "Device" section of /etc/X11/xorg.conf (    Option "XINERAMA" "off").

It will behave differently one way v the other.

Mark this thread SOLVED and fetch me that coffee lest I inform the DHS of your evil-doer attitude regarding the blessed bean.

---

### Post by Steven_B on 2009-11-20
Doesn't work for me.

I didn't run the script, since I prefer to use aptitude and install things manually so I have a better understanding of what I'm doing.
However, I basically followed it line-by line.

When I run
```

sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

I get:
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

```

When I take Firefox to a page containing Flash, it segfaults, with only the message "Segmentation fault."

I'm running Compiz on Ubuntu 9.10. The normal "flashplugin-installer" package works, but like herbertportillo, I can't click anything.

Here's the commands I ran:
> echo "Removing previous installs of flash:"
sudo aptitude purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo aptitude install ia32-libs nspluginwrapper

# Libraries
# libcurl3 CONFIRMED
# libnss3-1d CONFIRMED
# libnspr4-0d CONFIRMED

echo "Installing Flash Player 10"
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

# I get:
# nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so


echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

---

### Post by TheCowGod on 2009-11-20
[http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html)

Now you both owe me coffee =P

---

### Post by Steven_B on 2009-11-20
EDIT:
Duh, forgot the keyword "export".  Works great now.

----
No luck.
Tried adding "GDK_NATIVE_WINDOWS=1" to both
/usr/lib/nspluginwrapper/noarch/npviewer
and
/usr/lib/nspluginwrapper/i386/linux/npviewer
I was able to click once, but I don't know if that's a fluke or a variation of the bug.

---

