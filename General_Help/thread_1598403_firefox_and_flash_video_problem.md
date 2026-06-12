---
title: "firefox and flash video problem"
date: 2010-10-16
forum: General Help
---

### Post by warri0r on 2010-10-16
Recently i upgraded to maverick and since then video streaming sites are not at all working on firefox. say youtube, i tried purging firefox and reinstalled it but still the problem persists.

Thought of reinstalling flash plugin but its working fine on other browsers like google chrome. so wat is tat i have to do now, help plz

---

### Post by dougalkerr on 2010-10-16
Sorry I can't help much on this but, it will be interesting to see what comes of it. I would go hunting for the codecs pack and install, it can't do any harm.
I use Ultimate Edition myself and have no problems what so ever with codecs and such on any browsers. Never have and hopefully never will.
I won't go back to plain Ubuntu if I don't have to because I always seem to be installing codecs.
Everything is there and installed in UE - it just works.

For the sake of waiting till all packages are loaded, I will always use UE whenever possible. It isn't perfect but, almost. For me it is the operating system for now.

---

### Post by warri0r on 2010-10-16
nah, i dont think i need any codec for youtube and i dont have time to completely reinstall a new edition of ubuntu tat too for a simple problem :P do u really do that ?? lol. somebody get me real solution? plz help.

---

### Post by lovinglinux on 2010-10-17
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by gandaran on 2010-10-17
> **warri0r said:**
> Recently i upgraded to maverick and since then video streaming sites are not at all working on firefox. say youtube, i tried purging firefox and reinstalled it but still the problem persists.

Thought of reinstalling flash plugin but its working fine on other browsers like google chrome. so wat is tat i have to do now, help plz
you need to install adobe flash for firefox, google chrome works because it has built in adobe flash and firefox doesn't, install that flash-aid addon for firefox to sort things out

---

### Post by Cowchip7 on 2010-10-17
Flash Aid did the trick for me. Rock on.

---

### Post by warri0r on 2010-10-19
well, sadly this didnt work :( it reinstalled the flash app but it remains same, no stream video. really i didnt get any clue, someone do give a hand plz

---

### Post by lovinglinux on 2010-10-19
> **warri0r said:**
> well, sadly this didnt work :( it reinstalled the flash app but it remains same, no stream video. really i didnt get any clue, someone do give a hand plz

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by warri0r on 2010-10-20
dude, first of all thanks for spending your time in taking all those screenshots and and those shell commands. btw dood i m no newbie and no expert and i could understand plain things somehow lol so u could define me now :)


```
    File: /usr/lib/gnash/libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999.
    Gnash 0.8.8, the GNU SWF Player. 
```

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10
```



```
Ubuntu Architecture

Linux Nemesis 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
telepathy-ppa-maverick.list

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/gnash/libgnashplugin.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

Few screenshots, first 2 with **globally allow** settings for noscript. with tat it hung up. last pic with globally allow settings set to block and only few necessary site links were enabled, blocked the other links.

---

### Post by lovinglinux on 2010-10-20
> **warri0r said:**
> dude, first of all thanks for spending your time in taking all those screenshots and and those shell commands. btw dood i m no newbie and no expert and i could understand plain things somehow lol so u could define me now :)


```
    File: /usr/lib/gnash/libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999.
    Gnash 0.8.8, the GNU SWF Player. 
```

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10
```



```
Ubuntu Architecture

Linux Nemesis 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
telepathy-ppa-maverick.list

Flash packages

flashplugin-installer				install
flashplugin-nonfree				install

Plugin locations

/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/flashplugin-alternative.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/gnash/libgnashplugin.so'
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
```

Few screenshots, first 2 with **globally allow** settings for noscript. with tat it hung up. last pic with globally allow settings set to block and only few necessary site links were enabled, blocked the other links.

It seems you didn't use FLASH-AID properly, because you still have gnash installed, which is causing the problem. FLASH-AID removes that too. Click the extension icon in Firefox toolbar and select the option to install flash. It will remove gnash and will install the Adobe version, which will fix the problem.

---

### Post by warri0r on 2010-10-21
```
Please wait...DON'T CLOSE THIS TERMINAL!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lightspark
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash libboost-date-time1.42.0 gnash gnash-common
  libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash libboost-date-time1.42.0 gnash gnash-common
  libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash libboost-date-time1.42.0 gnash gnash-common
  libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash libboost-date-time1.42.0 flashplugin-installer gnash
  gnash-common libgtkglext1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 41.0kB disk space will be freed.
(Reading database ... 148374 files and directories currently installed.)
Removing flashplugin-nonfree ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash libboost-date-time1.42.0 gnash gnash-common
  libgtkglext1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 188kB disk space will be freed.
(Reading database ... 148371 files and directories currently installed.)
Removing flashplugin-installer ...
Purging configuration files for flashplugin-installer ...
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ maverick/partner Translation-en              
Ign http://archive.canonical.com/ maverick/partner Translation-en_IN           
Hit http://extras.ubuntu.com maverick Release.gpg                    
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IN           
Get:1 http://dl.google.com stable Release.gpg [191B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_IN    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_IN
Hit http://archive.ubuntu.com maverick-updates Release.gpg           
Hit http://archive.canonical.com maverick Release                    
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_IN
Hit http://archive.canonical.com maverick/partner i386 Packages      
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Get:2 http://dl.google.com stable Release [1,310B]                   
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_IN
Hit http://archive.ubuntu.com maverick-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Get:3 http://dl.google.com stable/main i386 Packages [979B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_IN
Hit http://archive.ubuntu.com maverick Release 
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://archive.ubuntu.com maverick-security Release
Hit http://archive.ubuntu.com maverick/main Sources
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Fetched 2,480B in 5s (486B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash libboost-date-time1.42.0 gnash gnash-common
  libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins msttcorefonts
  ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer flashplugin-nonfree
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/21.8kB of archives.
After this operation, 229kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-installer.
(Reading database ... 148360 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_10.1.85.3ubuntu1_i386.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.1.85.3ubuntu1_i386.deb) ...
Setting up flashplugin-installer (10.1.85.3ubuntu1) ...
Downloading...
--2010-10-21 20:07:50--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.85.3.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4884470 (4.7M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.85.3.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 34.9K 2m15s
    50K .......... .......... .......... .......... ..........  2% 52.2K 1m52s
   100K .......... .......... .......... .......... ..........  3% 55.3K 1m41s
   150K .......... .......... .......... .......... ..........  4% 58.2K 95s
   200K .......... .......... .......... .......... ..........  5% 58.1K 91s
   250K .......... .......... .......... .......... ..........  6% 58.0K 88s
   300K .......... .......... .......... .......... ..........  7% 90.2K 81s
   350K .......... .......... .......... .......... ..........  8% 38.5K 84s
   400K .......... .......... .......... .......... ..........  9% 64.9K 82s
   450K .......... .......... .......... .......... .......... 10% 46.9K 82s
   500K .......... .......... .......... .......... .......... 11% 39.9K 83s
   550K .......... .......... .......... .......... .......... 12% 50.1K 82s
   600K .......... .......... .......... .......... .......... 13% 53.6K 81s
   650K .......... .......... .......... .......... .......... 14% 50.8K 80s
   700K .......... .......... .......... .......... .......... 15% 55.2K 78s
   750K .......... .......... .......... .......... .......... 16% 58.2K 77s
   800K .......... .......... .......... .......... .......... 17% 59.3K 75s
   850K .......... .......... .......... .......... .......... 18% 59.5K 74s
   900K .......... .......... .......... .......... .......... 19% 79.1K 72s
   950K .......... .......... .......... .......... .......... 20% 63.1K 70s
  1000K .......... .......... .......... .......... .......... 22% 65.6K 69s
  1050K .......... .......... .......... .......... .......... 23% 80.4K 67s
  1100K .......... .......... .......... .......... .......... 24% 85.3K 65s
  1150K .......... .......... .......... .......... .......... 25% 65.8K 63s
  1200K .......... .......... .......... .......... .......... 26% 96.2K 62s
  1250K .......... .......... .......... .......... .......... 27% 63.7K 60s
  1300K .......... .......... .......... .......... .......... 28% 93.3K 59s
  1350K .......... .......... .......... .......... .......... 29% 86.7K 57s
  1400K .......... .......... .......... .......... .......... 30% 72.6K 56s
  1450K .......... .......... .......... .......... .......... 31% 49.7K 55s
  1500K .......... .......... .......... .......... .......... 32% 54.6K 55s
  1550K .......... .......... .......... .......... .......... 33% 45.0K 54s
  1600K .......... .......... .......... .......... .......... 34% 55.1K 54s
  1650K .......... .......... .......... .......... .......... 35% 67.5K 53s
  1700K .......... .......... .......... .......... .......... 36% 57.1K 52s
  1750K .......... .......... .......... .......... .......... 37% 62.0K 51s
  1800K .......... .......... .......... .......... .......... 38% 60.7K 50s
  1850K .......... .......... .......... .......... .......... 39% 79.2K 49s
  1900K .......... .......... .......... .......... .......... 40% 64.9K 48s
  1950K .......... .......... .......... .......... .......... 41% 77.4K 47s
  2000K .......... .......... .......... .......... .......... 42% 68.1K 46s
  2050K .......... .......... .......... .......... .......... 44% 80.1K 45s
  2100K .......... .......... .......... .......... .......... 45% 73.0K 44s
  2150K .......... .......... .......... .......... .......... 46% 86.2K 42s
  2200K .......... .......... .......... .......... .......... 47% 86.6K 41s
  2250K .......... .......... .......... .......... .......... 48% 74.9K 40s
  2300K .......... .......... .......... .......... .......... 49% 91.1K 39s
  2350K .......... .......... .......... .......... .......... 50% 89.8K 38s
  2400K .......... .......... .......... .......... .......... 51% 80.2K 37s
  2450K .......... .......... .......... .......... .......... 52% 94.9K 36s
  2500K .......... .......... .......... .......... .......... 53%  100K 35s
  2550K .......... .......... .......... .......... .......... 54% 86.6K 34s
  2600K .......... .......... .......... .......... .......... 55%  101K 33s
  2650K .......... .......... .......... .......... .......... 56%  105K 32s
  2700K .......... .......... .......... .......... .......... 57%  106K 31s
  2750K .......... .......... .......... .......... .......... 58%  106K 30s
  2800K .......... .......... .......... .......... .......... 59% 88.5K 29s
  2850K .......... .......... .......... .......... .......... 60%  108K 28s
  2900K .......... .......... .......... .......... .......... 61%  101K 27s
  2950K .......... .......... .......... .......... .......... 62%  106K 26s
  3000K .......... .......... .......... .......... .......... 63%  106K 26s
  3050K .......... .......... .......... .......... .......... 64%  110K 25s
  3100K .......... .......... .......... .......... .......... 66%  112K 24s
  3150K .......... .......... .......... .......... .......... 67%  114K 23s
  3200K .......... .......... .......... .......... .......... 68%  118K 22s
  3250K .......... .......... .......... .......... .......... 69%  116K 21s
  3300K .......... .......... .......... .......... .......... 70%  118K 20s
  3350K .......... .......... .......... .......... .......... 71%  121K 19s
  3400K .......... .......... .......... .......... .......... 72%  118K 19s
  3450K .......... .......... .......... .......... .......... 73%  114K 18s
  3500K .......... .......... .......... .......... .......... 74%  114K 17s
  3550K .......... .......... .......... .......... .......... 75%  117K 16s
  3600K .......... .......... .......... .......... .......... 76% 89.8K 16s
  3650K .......... .......... .......... .......... .......... 77%  120K 15s
  3700K .......... .......... .......... .......... .......... 78% 68.2K 14s
  3750K .......... .......... .......... .......... .......... 79% 66.5K 13s
  3800K .......... .......... .......... .......... .......... 80% 62.0K 13s
  3850K .......... .......... .......... .......... .......... 81% 60.0K 12s
  3900K .......... .......... .......... .......... .......... 82% 46.8K 11s
  3950K .......... .......... .......... .......... .......... 83% 71.0K 11s
  4000K .......... .......... .......... .......... .......... 84% 28.1K 10s
  4050K .......... .......... .......... .......... .......... 85% 26.6K 10s
  4100K .......... .......... .......... .......... .......... 87% 29.2K 9s
  4150K .......... .......... .......... .......... .......... 88% 48.1K 8s
  4200K .......... .......... .......... .......... .......... 89% 38.2K 8s
  4250K .......... .......... .......... .......... .......... 90% 52.1K 7s
  4300K .......... .......... .......... .......... .......... 91% 38.7K 6s
  4350K .......... .......... .......... .......... .......... 92% 54.1K 6s
  4400K .......... .......... .......... .......... .......... 93% 57.2K 5s
  4450K .......... .......... .......... .......... .......... 94% 59.7K 4s
  4500K .......... .......... .......... .......... .......... 95% 58.2K 3s
  4550K .......... .......... .......... .......... .......... 96% 79.1K 3s
  4600K .......... .......... .......... .......... .......... 97% 61.8K 2s
  4650K .......... .......... .......... .......... .......... 98% 59.0K 1s
  4700K .......... .......... .......... .......... .......... 99% 88.4K 0s
  4750K .......... .........                                  100% 53.8K=73s

2010-10-21 20:09:05 (65.7 KB/s) - `./adobe-flashplugin_10.1.85.3.orig.tar.gz' saved [4884470/4884470]

Download done.
Flash Plugin installed.
Setting up flashplugin-nonfree (10.1.85.3ubuntu1) ...
Finished! You can close this terminal. You must restart Firefox now.

```

```
    File: /usr/lib/gnash/libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999.
    Gnash 0.8.8, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see http://www.gnu.org/software/gnash.
    Compatible Shockwave Flash 10.1 r999.
```

i reinstalled again and here is the output. any clue? :(

---

### Post by lovinglinux on 2010-10-22
> **warri0r said:**
> ```
    File: /usr/lib/gnash/libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999.
    Gnash 0.8.8, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see http://www.gnu.org/software/gnash.
    Compatible Shockwave Flash 10.1 r999.
```

i reinstalled again and here is the output. any clue? :(

Yes. They changed the gnash package name in Maverick to **browser-plugin-gnash** and **mozilla-plugin-gnash** is just a dummy now. So I need to update the extension.

To solve your problem run this:

```
sudo apt-get purge browser-plugin-gnash
```

---

### Post by Steve R. on 2010-10-22
Upgrading to Ubuntu 10.10 wiped-out my ability to listen to streaming audio with Firefox. I got around to checking my CPU usage and saw that GNU SWF Player was hogging the CPU Cycles. Did a search here and found that GNU was the apparent culprit. Removed it and the audio is coming in fine now.

---

### Post by warri0r on 2010-10-23
> **lovinglinux said:**
> Yes. They changed the gnash package name in Maverick to **browser-plugin-gnash** and **mozilla-plugin-gnash** is just a dummy now. So I need to update the extension.

To solve your problem run this:

```
sudo apt-get purge browser-plugin-gnash
```

works now :) thanks dude

---

### Post by lovinglinux on 2010-10-23
> **warri0r said:**
> works now :) thanks dude

No problem. BTW, Mozilla has already approved the new version of FLASH-AID, which solves this particular problem.

---

### Post by Tiddens on 2010-10-28
Guys - There just can't be updates that ruin the operation of PC's! We are using 9.1, it was working fine for the last year, and now when it is streaming the picture pauses and goes black every 2 minutes! We are trying to sell an Internet TV product, The Wave at CatchTheWaveTV.com, but how can we go into production if this happens? We tried Ubuntu 10, but the streaming is much slower and not acceptable. Sorry - All computer programs I've known over 30 years get better with each version. I am getting the impression that versions of Ubuntu are totally different and each have very basic problems. So why promote a certain version on the website, such as 10? Why not list the versions and say what their pros and cons are, so people can decide which one they want? We will try the Flash-Aid fix, and/or install and use Chrome instead of Firefox.  I just had someone tell me that Hardy 8.04 was the only good version of Ubuntu. Do we need to go back and do a complete software build on Hardy and see if it has any problems? I'm really trying to be an Ubuntu promoter with a volume product, and really don't want to use Windows for so many reasons...

---

### Post by Tiddens on 2010-10-28
Well, Flash-Aid didn't fix the pausing in Firefox...  We will look into using Chrome instead...

---

### Post by Tiddens on 2010-10-28
Well, the videos pause and black out every 2 minutes in Chrome also, so it must have been a bad update to Ubuntu 9?  This really isn't nice...

---

### Post by lovinglinux on 2010-10-29
> **Tiddens said:**
> Well, the videos pause and black out every 2 minutes in Chrome also, so it must have been a bad update to Ubuntu 9?  This really isn't nice...

See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Tiddens on 2010-10-29
Thanks "lovinglinux"!  I tried the folllowing ideas, but they didn't stop the pausing every two minutes (screen freezes for one second, then goes black for two seconds).
 
[COLOR=#333333][COLOR=#990000]**Code:**[/COLOR]
[COLOR=#666666][[COLOR=#336699]?[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html#")
1
2
3
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/



[/COLOR]
[/COLOR]


Restart the browser.

If that doesn't work, then right-click the flash video, select "Settings", then untick the option "Enable hardware acceleration".

---

### Post by Tiddens on 2010-11-01
This is very bad.  An update to 9.10 has caused the video streaming to pause and the screen to go black every 2 minutes for about 2 seconds.  I just tried a clean hard drive and new installation of 9.10, and confirmed it is a basic problem with Ubuntu (happens with both Firefox and Chrome as noted above).  So, we can't use 9.10, 10.04 streaming is very slow, so we will try 8.04.  We are really trying to use Ubuntu in our production product!

---

### Post by Tiddens on 2010-11-02
Note that I have elevated this issue to a new thread:  [http://ubuntuforums.org/showthread.php?p=10059455#post10059455](http://ubuntuforums.org/showthread.php?p=10059455#post10059455)

---

### Post by Futurian on 2010-11-04
lovinglinux,

Your fix worked for me.

Thanks!

---

### Post by lovinglinux on 2010-11-04
> **Futurian said:**
> lovinglinux,

Your fix worked for me.

Thanks!

You are welcome.

---

### Post by bluepicaso on 2010-11-14
> **lovinglinux said:**
> Yes. They changed the gnash package name in Maverick to **browser-plugin-gnash** and **mozilla-plugin-gnash** is just a dummy now. So I need to update the extension.

To solve your problem run this:

```
sudo apt-get purge browser-plugin-gnash
```


awesome solution

---

### Post by cees.knysna on 2010-11-15
Thanks so much.
I had exactly the same problem as Warrior.
Your help was the only one with good result.
cees.knysna

---

