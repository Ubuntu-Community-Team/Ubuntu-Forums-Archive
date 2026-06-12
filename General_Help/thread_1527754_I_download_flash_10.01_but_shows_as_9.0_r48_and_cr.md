---
title: "I download flash 10.01 but shows as 9.0 r48 and crashes"
date: 2010-07-09
forum: General Help
---

### Post by Anzan on 2010-07-09
Hi.

I have Firefox 3.6.6 (for Ubuntu canonical -1.0) in 10.04.

Adobe Flash crashes. I've uninstalled and reinstalled through CLI, through Synaptic, through Adobe's website using the .deb. and Apturl. As it's a shared extension for Epiphany-browser and Chrome I've uninstalled and the completely uninstalled them.

I'm out of ideas. Please offer any suggestions.

---

### Post by davidmohammed on 2010-07-09
is this for 64bit lucid or 32bit lucid?

---

### Post by Anzan on 2010-07-09
32bit lucid, davidmohammed.

---

### Post by davidmohammed on 2010-07-09
obviously you've got some trace of flash on your system.

try removing all traces by running through the following.

sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so

sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm 
sudo dpkg-reconfigure adobe-flashplugin --force 
sudo dpkg --purge --force-all adobe-flashplugin 
sudo apt-get install flashplugin-nonfree

---

### Post by Anzan on 2010-07-09
Unfortunately the problem persists. Thank you very much though.

---

### Post by Anzan on 2010-07-09
When I cd to /usr/lib/mozilla/plugins/

:/usr/lib/mozilla/plugins$ ls
flashplugin-alternative.so  librhythmbox-itms-detection-plugin.so  libtotem-mully-plugin.so
gxineplugin.so              libtotem-cone-plugin.so                libtotem-narrowspace-plugin.so
libjavaplugin.so            libtotem-gmp-plugin.so                 xineplugin.so

Is flashplugin-alternative.so the problem? But it's what was installed following your directions...


Edit:

The history shows 

2010-07-09 18:49:03 (496 KB/s) - `./adobe-flashplugin_10.1.53.64.orig.tar.gz' saved [4739416/4739416]

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.1.53.64ubuntu0.10.04.3) ...

Very strange.

---

### Post by davidmohammed on 2010-07-10
do a 

sudo apt-get remove flashplugin-nonfree

then as you have discovered see if that alternate.so file is still there.  Remove it if it is

also

start up firefox and do a 

```
about:plugins
```

see if "shockwave flash" or "flash" is installed still.

if it is, close down firefox and from the command line, start firefox with a new profile

firefox -P

create a profile and repeat the ```
about:plugins
```

see if the flash plugin is still there.  If it is not, then your flash plugin is stored somewhere in your profile...

---

### Post by Anzan on 2010-07-10
Yes. It was in the profile.

Even after removing it there were further complications which I won't go into but it's installed and working now. 

Thank you very much for your help.

---

### Post by danishbacker on 2010-09-04
same problem here

In my case things like farmville game and youtube videos were very slow when played in fullscreen. So after reading few forums I found that flash palyer 9r48 (install_flash_player_9r48_linux.tar.gz) has no problems like flash player 10. Then after installing flash 9r48 things gone even worse "Flash payer Crash!"
then after removing that I installed the latest flash. But there was problem.

the flash 9r48 was still residing in the following location and making troubles.
when i checked "about: plugins" in ff there was two flash players installed. 10 and 9

/home/user/.mozilla/plugins/libflashplayer.so

the problem was solved by deleting the above file from there.

One more at all these time flash apps in google chrome was running perfect may be because of its faster webkit engine. I think the problem is with Mozilla and Flash.

:| lengthy story right!
thought this would help newbies like me...

---

### Post by cbciv on 2010-11-15
> **danishbacker said:**
> 

the flash 9r48 was still residing in the following location and making troubles.
when i checked "about: plugins" in ff there was two flash players installed. 10 and 9

/home/user/.mozilla/plugins/libflashplayer.so

the problem was solved by deleting the above file from there.


I had tried uninstalling Flash but kept seeing 9.0 r48 in Firefox anyway.  When I checked, I found that same file and removed it, then reinstalled version 10 using the .deb package (I'm on Hardy).  Flash 10 is now being loaded by Firefox and is working correctly.

Thanks for posting this, danishbacker.

---

