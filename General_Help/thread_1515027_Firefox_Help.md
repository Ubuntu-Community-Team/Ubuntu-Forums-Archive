---
title: "Firefox Help"
date: 2010-06-21
forum: General Help
---

### Post by jschille on 2010-06-21
Hello,
I recently did something to my firefox and now everytime I go to certain webpages my Firefox freezes (turns grey) and I have to force quit the program, so lately I have been using Opera (which I don't like as much as Firefox, probably just more used to Firefox).

Anyway, I would like to COMPLETELY remove firefox and then reinstall firefox and see if that fixes the problem.

What is the easiest way to remove firefox completely and then reinstall it?

Thanks for the help. Im sure this is an easy solution, I just want to make sure that I am doing a complete fresh install.

EDIT:
I seem to be making some kind of progress.  Instead of doing a fresh install I ran the command
```
firefox -safe-mode
``` and reset everything to default mode and then ran the command 
```
sudo apt-get install ubuntu-restricted-extras
```
although, at the very end of the install i get errors...
```
jb@jb-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for jb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libkworkspace4 libplasma-geolocation-interface4 libplasmaclock4
  libweather-ion4 kdebase-workspace-bin mysql-server-core-5.1 libprocessui4
  libprocesscore4 akonadi-server libksgrd4 libtaskmanager4 libqimageblitz4
  mysql-client-core-5.1 kdebase-workspace-data libplasmagenericshell4
  kdebase-workspace-kgreet-plugins libkephal4 plasma-dataengines-workspace
  ksysguardd libkscreensaver5 libkfontinst4 libplasma-applet-system-monitor4
  kdepim-runtime plasma-widgets-workspace
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up flashplugin-installer (10.1.53.64ubuntu0.10.04.1) ...
Downloading...
--2010-06-21 17:02:32--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.53.64.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4739416 (4.5M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.1.53.64.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 62.4K 73s
    50K .......... .......... .......... .......... ..........  2%  236K 46s
   100K .......... .......... .......... .......... ..........  3%  278K 36s
   150K .......... .......... .......... .......... ..........  4%  610K 28s
   200K .......... .......... .......... .......... ..........  5%  385K 25s
   250K .......... .......... .......... .......... ..........  6%  635K 21s
   300K .......... .......... .......... .......... ..........  7%  612K 19s
   350K .......... .......... .......... .......... ..........  8%  463K 18s
   400K .......... .......... .......... .......... ..........  9%  603K 16s
   450K .......... .......... .......... .......... .......... 10%  636K 15s
   500K .......... .......... .......... .......... .......... 11%  112K 17s
   550K .......... .......... .......... .......... .......... 12% 2.25M 15s
   600K .......... .......... .......... .......... .......... 14%  258K 15s
   650K .......... .......... .......... .......... .......... 15% 3.52M 14s
   700K .......... .......... .......... .......... .......... 16% 3.95M 13s
   750K .......... .......... .......... .......... .......... 17%  260K 13s
   800K .......... .......... .......... .......... .......... 18%  209K 13s
   850K .......... .......... .......... .......... .......... 19%  229K 13s
   900K .......... .......... .......... .......... .......... 20%  228K 13s
   950K .......... .......... .......... .......... .......... 21%  217K 13s
  1000K .......... .......... .......... .......... .......... 22% 2.34M 12s
  1050K .......... .......... .......... .......... .......... 23%  228K 12s
  1100K .......... .......... .......... .......... .......... 24%  233K 12s
  1150K .......... .......... .......... .......... .......... 25% 2.10M 12s
  1200K .......... .......... .......... .......... .......... 27%  237K 12s
  1250K .......... .......... .......... .......... .......... 28%  226K 12s
  1300K .......... .......... .......... .......... .......... 29%  217K 12s
  1350K .......... .......... .......... .......... .......... 30% 73.2K 13s
  1400K .......... .......... .......... .......... .......... 31%  212K 12s
  1450K .......... .......... .......... .......... .......... 32%  146M 12s
  1500K .......... .......... .......... .......... .......... 33%  141M 11s
  1550K .......... .......... .......... .......... .......... 34%  154M 11s
  1600K .......... .......... .......... .......... .......... 35%  112K 11s
  1650K .......... .......... .......... .......... .......... 36%  198K 11s
  1700K .......... .......... .......... .......... .......... 37%  226K 11s
  1750K .......... .......... .......... .......... .......... 38%  107K 11s
  1800K .......... .......... .......... .......... .......... 39%  220K 11s
  1850K .......... .......... .......... .......... .......... 41%  217K 11s
  1900K .......... .......... .......... .......... .......... 42%  223K 11s
  1950K .......... .......... .......... .......... .......... 43%  220K 10s
  2000K .......... .......... .......... .......... .......... 44%  210K 10s
  2050K .......... .......... .......... .......... .......... 45% 1.18M 10s
  2100K .......... .......... .......... .......... .......... 46%  224K 10s
  2150K .......... .......... .......... .......... .......... 47%  311K 10s
  2200K .......... .......... .......... .......... .......... 48%  610K 9s
  2250K .......... .......... .......... .......... .......... 49%  300K 9s
  2300K .......... .......... .......... .......... .......... 50%  341K 9s
  2350K .......... .......... .......... .......... .......... 51%  528K 8s
  2400K .......... .......... .......... .......... .......... 52%  324K 8s
  2450K .......... .......... .......... .......... .......... 54%  343K 8s
  2500K .......... .......... .......... .......... .......... 55%  554K 8s
  2550K .......... .......... .......... .......... .......... 56%  323K 8s
  2600K .......... .......... .......... .......... .......... 57%  333K 7s
  2650K .......... .......... .......... .......... .......... 58%  538K 7s
  2700K .......... .......... .......... .......... .......... 59%  301K 7s
  2750K .......... .......... .......... .......... .......... 60%  616K 7s
  2800K .......... .......... .......... .......... .......... 61%  313K 6s
  2850K .......... .......... .......... .......... .......... 62%  338K 6s
  2900K .......... .......... .......... .......... .......... 63%  464K 6s
  2950K .......... .......... .......... .......... .......... 64%  355K 6s
  3000K .......... .......... .......... .......... .......... 65%  522K 6s
  3050K .......... .......... .......... .......... .......... 66%  330K 5s
  3100K .......... .......... .......... .......... .......... 68%  392K 5s
  3150K .......... .......... .......... .......... .......... 69%  463K 5s
  3200K .......... .......... .......... .......... .......... 70%  370K 5s
  3250K .......... .......... .......... .......... .......... 71%  136K 5s
  3300K .......... .......... .......... .......... .......... 72%  255K 5s
  3350K .......... .......... .......... .......... .......... 73%  147M 4s
  3400K .......... .......... .......... .......... .......... 74%  593K 4s
  3450K .......... .......... .......... .......... .......... 75%  178K 4s
  3500K .......... .......... .......... .......... .......... 76%  189K 4s
  3550K .......... .......... .......... .......... .......... 77%  219K 4s
  3600K .......... .......... .......... .......... .......... 78%  242K 3s
  3650K .......... .......... .......... .......... .......... 79%  224K 3s
  3700K .......... .......... .......... .......... .......... 81%  156K 3s
  3750K .......... .......... .......... .......... .......... 82% 94.8K 3s
  3800K .......... .......... .......... .......... .......... 83%  113K 3s
  3850K .......... .......... .......... .......... .......... 84%  215K 3s
  3900K .......... .......... .......... .......... .......... 85%  210K 3s
  3950K .......... .......... .......... .......... .......... 86%  227K 2s
  4000K .......... .......... .......... .......... .......... 87%  212K 2s
  4050K .......... .......... .......... .......... .......... 88%  217K 2s
  4100K .......... .......... .......... .......... .......... 89%  214K 2s
  4150K .......... .......... .......... .......... .......... 90%  116K 2s
  4200K .......... .......... .......... .......... .......... 91%  226K 1s
  4250K .......... .......... .......... .......... .......... 92%  206K 1s
  4300K .......... .......... .......... .......... .......... 93%  229K 1s
  4350K .......... .......... .......... .......... .......... 95%  217K 1s
  4400K .......... .......... .......... .......... .......... 96%  219K 1s
  4450K .......... .......... .......... .......... .......... 97%  207K 1s
  4500K .......... .......... .......... .......... .......... 98%  224K 0s
  4550K .......... .......... .......... .......... .......... 99%  116K 0s
  4600K .......... .......... ........                        100% 2.73M=18s

2010-06-21 17:02:51 (252 KB/s) - `./adobe-flashplugin_10.1.53.64.orig.tar.gz' saved [4739416/4739416]

Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
jb@jb-laptop:~$ 

```

Any ideas on how to fix these errors?

---

### Post by Pollox on 2010-06-22
To completely remove firefox, use "sudo apt-get purge firefox" or select the "Mark for complete removal option" in Synaptic.  In reading your error message, it seems to want you to install flashplugin-installer first.  Personally, I have adobe-flashplugin installed instead.

---

### Post by lovinglinux on 2010-06-22
Go to "System >> Administration >> Software Sources >> Other software" and disable the partner repository. Then run these commands.

```
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

For more info about those commands see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

To fix Firefox see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by jschille on 2010-06-24
> **lovinglinux said:**
> Go to "System >> Administration >> Software Sources >> Other software" and disable the partner repository. Then run these commands.

```
sudo apt-get purge swfdec-mozilla
sudo apt-get purge mozilla-plugin-gnash
sudo apt-get purge adobe-flashplugin
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
rm -f $HOME/.mozilla/plugins/*flash*so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo apt-get install flashplugin-nonfree
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

For more info about those commands see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

To fix Firefox see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).


I appreciate the help, just not sure on how to complete the 1st step.  What box am i checking? I have quite a few options.  Just don't want to click on the wrong one.  After I run the commands am I coming back and checking the box again?  Not sure if it matters, but im running a 64 bit os

---

### Post by guyshoxton on 2010-06-24
May i suggest re installing firefox?

---

### Post by lovinglinux on 2010-06-25
> **jschille said:**
> I appreciate the help, just not sure on how to complete the 1st step.  What box am i checking? I have quite a few options.  Just don't want to click on the wrong one.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161500&stc=1&d=1277452378[/IMG]

> **jschille said:**
> After I run the commands am I coming back and checking the box again?

Yes, you can do that.

> **jschille said:**
> Not sure if it matters, but im running a 64 bit os

It matters, but Adobe is not supporting the 64bit version of flash anymore, so the command will install the 32bit.

---

