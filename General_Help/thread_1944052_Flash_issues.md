---
title: "Flash issues"
date: 2012-03-20
forum: General Help
---

### Post by HenryL on 2012-03-20
Since the latest update of Flash I've had problems with it not working. I am running Ubuntu 11.10.

To try to solve the problem I installed Flash Aid as recommended in these forums. It installed the Adobe Beta option and I went with all its default settings. 

The result is that Flash-based web elements now work, however movies have no sound and play at three to five times normal speed. Its as though they were set to no volume and run on fast forward. The problem obtains with both Firefox and Chromium.

I therefore tried the other Flash versions that Flash Aid offers. These did not work at all. I've reinstalled Adobe Beta...but it would be nice if Flash just worked like it used to!

Any suggestions would be appreciated.

---

### Post by lovinglinux on 2012-03-21
Please generate a Report using Flash-Aid Help menu and post here.

---

### Post by HenryL on 2012-03-21
Thanks! Here is the report:

```
Ubuntu Architecture  Linux ubuntu 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux  Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10"  

Firefox Packages  

firefox						
firefox-globalmenu				
firefox-gnome-support				
firefox-locale-en


Firefox binaries  

/usr/bin/firefox 
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

chris-lea-node_js-oneiric.list 
chris-lea-node_js-oneiric.list.save 
deluge-team-ppa-natty.list 
deluge-team-ppa-natty.list.distUpgrade 
deluge-team-ppa-natty.list.save 
getdeb.list getdeb.list.bck 
getdeb.list.distUpgrade 
getdeb.list.save 
medibuntu.list 
medibuntu.list.distUpgrade 
medibuntu.list.save 
playdeb.list 
playdeb.list.distUpgrade 
playdeb.list.save 
tualatrix-ppa-natty.list 
tualatrix-ppa-natty.list.distUpgrade 
tualatrix-ppa-natty.list.save 
ubuntu-audio-dev-ppa-oneiric.list 
ubuntu-audio-dev-ppa-oneiric.list.save 
ubuntu-wine-ppa-natty.list 
ubuntu-wine-ppa-natty.list.distUpgrade 
ubuntu-wine-ppa-natty.list.save 
webupd8team-sublime-text-2-oneiric.list 
webupd8team-sublime-text-2-oneiric.list.save 
wfg-0ad-natty.list 
wfg-0ad-natty.list.distUpgrade 
wfg-0ad-natty.list.save  

Flash packages  

adobe-flash-properties-gtk			
adobe-flashplugin				

Plugin locations  

/home/henrylauer/.cache/.fr-ycg2Ti/libflashplayer.so 
/usr/lib/adobe-flashplugin/libflashplayer.so  
/usr/lib/firefox/plugins/flashplugin-alternative.so 
/usr/lib/iceape/plugins/flashplugin-alternative.so 
/usr/lib/iceweasel/plugins/flashplugin-alternative.so 
/usr/lib/midbrowser/plugins/flashplugin-alternative.so 
/usr/lib/mozilla/plugins/flashplugin-alternative.so 
/usr/lib/xulrunner/plugins/flashplugin-alternative.so 
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' 
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' 
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped 
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat
```

---

### Post by lovinglinux on 2012-03-22
> **HenryL said:**
> Thanks! Here is the report:

```
Ubuntu Architecture  Linux ubuntu 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux  Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10"  

Firefox Packages  

firefox						
firefox-globalmenu				
firefox-gnome-support				
firefox-locale-en


Firefox binaries  

/usr/bin/firefox 
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

chris-lea-node_js-oneiric.list 
chris-lea-node_js-oneiric.list.save 
deluge-team-ppa-natty.list 
deluge-team-ppa-natty.list.distUpgrade 
deluge-team-ppa-natty.list.save 
getdeb.list getdeb.list.bck 
getdeb.list.distUpgrade 
getdeb.list.save 
medibuntu.list 
medibuntu.list.distUpgrade 
medibuntu.list.save 
playdeb.list 
playdeb.list.distUpgrade 
playdeb.list.save 
tualatrix-ppa-natty.list 
tualatrix-ppa-natty.list.distUpgrade 
tualatrix-ppa-natty.list.save 
ubuntu-audio-dev-ppa-oneiric.list 
ubuntu-audio-dev-ppa-oneiric.list.save 
ubuntu-wine-ppa-natty.list 
ubuntu-wine-ppa-natty.list.distUpgrade 
ubuntu-wine-ppa-natty.list.save 
webupd8team-sublime-text-2-oneiric.list 
webupd8team-sublime-text-2-oneiric.list.save 
wfg-0ad-natty.list 
wfg-0ad-natty.list.distUpgrade 
wfg-0ad-natty.list.save  

Flash packages  

adobe-flash-properties-gtk			
adobe-flashplugin				

Plugin locations  

/home/henrylauer/.cache/.fr-ycg2Ti/libflashplayer.so 
/usr/lib/adobe-flashplugin/libflashplayer.so  
/usr/lib/firefox/plugins/flashplugin-alternative.so 
/usr/lib/iceape/plugins/flashplugin-alternative.so 
/usr/lib/iceweasel/plugins/flashplugin-alternative.so 
/usr/lib/midbrowser/plugins/flashplugin-alternative.so 
/usr/lib/mozilla/plugins/flashplugin-alternative.so 
/usr/lib/xulrunner/plugins/flashplugin-alternative.so 
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' 
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' 
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped 
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat
```

I can't see any problems with flash installation. However I would run this to delete a shared object stored in cache.

```
rm -f /home/henrylauer/.cache/.fr-ycg2Ti/libflashplayer.so 
```

Then open Firefox, type **about:config** in the address bar, then type **plugin.expose_full_path** in the filter. Double-click the resulting entry to set it as true.

The type **[noparse]about:plugins[/noparse]** in the address bar. Check if you see a Flash plugin listed. It should be just one.

---

### Post by HenryL on 2012-03-22
Ok, followed your instructions. Unfortunately...no change in the behavior of Flash :(

---

### Post by lovinglinux on 2012-03-22
> **HenryL said:**
> Ok, followed your instructions. Unfortunately...no change in the behavior of Flash :(

Did you find a Flash player in [noparse]about:plugins[/noparse]?

---

### Post by HenryL on 2012-03-22
Oops, yes, so I did. Screenshot attached.

---

### Post by lovinglinux on 2012-03-22
Please try the fifth item on the following list:

[http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)

---

### Post by HenryL on 2012-03-23
Ok...I hit a snag, to whit:

```
henrylauer@ubuntu:~$ sudo apt-get install asound-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package asound-gtk
```Also, with the last step, how do I find this location? I don't seem to have a system>preferences area:

> Then go to System >> Preferences >> Default Sound Card  and  ensure that PulseAudio is selected, and restart your browser.Thanks!

H

---

### Post by lovinglinux on 2012-03-23
> **HenryL said:**
> Ok...I hit a snag, to whit:

```
henrylauer@ubuntu:~$ sudo apt-get install asound-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package asound-gtk
```Also, with the last step, how do I find this location? I don't seem to have a system>preferences area:

Thanks!

H

Sorry, the tutorial is for old versions of Ubuntu. Just ignore the last two steps. If it doesn't solve the problem, try to disable hardware acceleration from Flash settings. You can do that by right-clicking on a YouTube video.

---

### Post by punkybouy on 2012-03-24
I have similar problems and decided to go with Google Chrome which works just fine.

---

### Post by HenryL on 2012-03-25
Ok...well I cant seem to figure out how to disable hardware acceleration.

So the hardware acceleration is in the settings option right? Because when I click that it brings up the settings window but it is frozen and I cannot do anything further with it :(

---

### Post by lovinglinux on 2012-03-26
> **HenryL said:**
> Ok...well I cant seem to figure out how to disable hardware acceleration.

So the hardware acceleration is in the settings option right? Because when I click that it brings up the settings window but it is frozen and I cannot do anything further with it :(

Yes. Try with a different browser.

---

### Post by HenryL on 2012-03-26
Same issue with Chromium :(

---

### Post by HenryL on 2012-04-04
Anyone? Ideas? Is there something other than Flash Player I can use to view these files, for example?

---

### Post by lovinglinux on 2012-04-05
> **HenryL said:**
> Ok...well I cant seem to figure out how to disable hardware acceleration.

So the hardware acceleration is in the settings option right? Because when I click that it brings up the settings window but it is frozen and I cannot do anything further with it :(

Do that while viewing the video in fullscreen.

---

### Post by HenryL on 2012-04-05
Ok! Well that worked, hardware acceleration disabled.

Only...still no sound, still playing at super-speed :(

---

