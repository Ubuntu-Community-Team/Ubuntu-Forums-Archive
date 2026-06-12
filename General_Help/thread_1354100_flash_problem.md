---
title: "flash problem"
date: 2009-12-13
forum: General Help
---

### Post by Kmob810 on 2009-12-13
Hi friends. I need a bit of help please. I am running 9.04 and when I try to open Farmville I am informed that I need to upgrade Flash. When I download the latest version and attempt to install it I am informed that it is already installed.  I am at a loss as to what is happening. This only happened when I upgraded from 8.10. I can open YouTube its just Farmville which is causing the problem (I think!)
Can anyone help?

---

### Post by lidex on 2009-12-13
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

That is, if you're using Firefox. Also try it with a different browser. No idea what "Farmville" is.

---

### Post by Uachtarain on 2009-12-13
Install Google Chrome.... Remove other browsers or leave them??. This problem has been with Firefox and has been for a couple of years now. Not worth the time to fix.

Fergal

---

### Post by lidex on 2009-12-13
> **Uachtarain said:**
> Install Google Chrome.... Remove other browsers or leave them??. This problem has been with Firefox and has been for a couple of years now. Not worth the time to fix.

Fergal

If it doesn't work for you uninstall it.

---

### Post by Johnny B on 2009-12-13
firefox isin't the problem and chrome has its own set of problems.
fix the flash problem.


go to [http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
select tar.gz fo linux and download
extract libflashplayer.so from the tar.gz file
save this script in the same directory as libflashplayer.so
chmod +x scriptname
then run script with sudo
done, post results.

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Edited by Jordan Loehr jordan.loehr@gmail.com

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
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

cd /etc/
mkdir adobe
sudo touch /etc/adobe/mms.cfg
sudo echo "OverrideGPUValidation=true" > /etc/adobe/mms.cfg
exit

```

---

### Post by James Dee on 2009-12-14
maybe you have problems with java...

[http://forum.playfish.com/showthread.php?t=1254326](http://forum.playfish.com/showthread.php?t=1254326)

---

