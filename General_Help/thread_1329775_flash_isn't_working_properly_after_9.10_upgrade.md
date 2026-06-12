---
title: "flash isn't working properly after 9.10 upgrade"
date: 2009-11-17
forum: General Help
---

### Post by jchysk on 2009-11-17
Just upgraded from 9.04 to 9.10 about 40 minutes ago. Opened firefox and immediately noticed flash was no longer working for any video player. Just big black boxes where flash should be. Googled the problem but couldn't find many similar issues, most people have control issues, sound issues, or installation issues. I have flashplugin-installer and flashplugin-nonfree installed. The only things I've tried so far is removing them completely then reinstalling and installing flash 10.1. I'm unsure of what I should try now.

---

### Post by fluffman86 on 2009-11-17
Use synaptic to completely remove, or purge, the flashplugin-nonfree and flashplugin-installer apps, then try to get the latest version from adobe's website.  I believe they offer a .deb now, so you'll want that.

If that fails, run this command to rename you firefox profile folder, and see if the problem is with firefox:
mv ~/.mozilla/firefox/*.default ~/.mozilla/firefox/profilebackup

Also consider trying another browser, like opera or chromium from [http://launchpad.net/~chromium-daily/+archive/ppa](http://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by jchysk on 2009-11-17
I've been trying a few things out. I removed flashplugin and tried installing swfdec-mozilla. I tried 
```
sudo apt-get remove flashplugin-installer flashplugin-nonfree swdec-mozilla mozilla-plugin-gnash
cd /tmp
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```
after that which I found on [http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/](http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/)
My problem persisted but something that's bothering me now is that when I go to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) my flash version has been 10,1,999,0 throughout. When I did the last reinstallation of flash it should have changed back to 10,0,32,18 so I feel like I have an installation of Flash now that won't go away.

---

### Post by blueridgedog on 2009-11-17
Are you running the 64 bit version or the 32 bit version?

---

### Post by fancypiper on 2009-11-17
Do you have a 64 bit processor?

---

### Post by jchysk on 2009-11-17
> **fluffman86 said:**
> Use synaptic to completely remove, or purge, the flashplugin-nonfree and flashplugin-installer apps, then try to get the latest version from adobe's website.  I believe they offer a .deb now, so you'll want that.

If that fails, run this command to rename you firefox profile folder, and see if the problem is with firefox:
mv ~/.mozilla/firefox/*.default ~/.mozilla/firefox/profilebackup

Also consider trying another browser, like opera or chromium from [http://launchpad.net/~chromium-daily/+archive/ppa](http://launchpad.net/~chromium-daily/+archive/ppa)

Thanks for responding, fluffman. Right now I have flashplugin completely removed, but everything is exactly the same as before. It seems like Flash is still installed somewhere, so I'm trying to figure that out. I can't install the .deb because 64-bit. I tried moving my profiles to a backup folder and when I open firefox it says firefox is already running and won't open until I restore the profile. I don't know what's up with that either.

---

### Post by jchysk on 2009-11-17
Yes. 64-bit processor.

---

### Post by jchysk on 2009-11-17
So flashplugin is completely removed and I manually removed all the .so plugins from the /usr/lib/mozilla/plugins directory and if I go to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) it still says Flash Player is successfully installed at version 10,1,999,0.

---

### Post by fancypiper on 2009-11-17
This should install the 64 bit flash version:
```
#!/bin/bash

## First we make the working directory
sudo mkdir /tmp/pluginstall

#choose version of ubuntu
#Input code browser
function strinput {
 unset refstr
 echo -n "$1"
 read refstr
}

## Ask if they agree to file bug reports, sort of a reminder
echo
echo " This script is used to setup the Flash 10 Alpha. "
echo " By entering yes below you acknowlage that you "
echo " are installing development software and you "
echo " will file bug reports with Adobe for every "
echo " problem you incounter."
echo
echo " Do you agree? yes or no : "


if [ "$installtype" = "" ]
then
 echo -n "(please type the whole word in lower case letters)"
 strinput
else
 refstr=$installtype
fi

if [ "$refstr" = "yes" ]
then
 echo "Flash installing."


## First we uninstall and remove all the existing flash packages

# No longer trying to reply nspluginwrapper since Acrobat Reader 9 requires it
#sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
#sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so

## Then we make a temp folder and download the new plugin
cd /tmp/pluginstall
sudo wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz

## Next we extract and place the plugin
sudo tar xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Please restart Firefox to enable Flash"

elif [ "$refstr" = "no" ]
then
 echo "I am sorry but you have to agree. "

else
 echo  " I am sorry but you have to agree. "
 echo
fi

```

Save that as get64bitflash, chmod 755 and execute as root, then restart your browser.

---

### Post by jchysk on 2009-11-17
Yay I figured it out. Thanks for the response fancypiper. I think your script would've solved it for me too because my problem was I needed to remove gnash. After I removed that I reinstalled flashplugin and everything works again.

---

