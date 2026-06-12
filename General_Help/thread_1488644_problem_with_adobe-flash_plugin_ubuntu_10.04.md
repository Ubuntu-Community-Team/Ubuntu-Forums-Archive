---
title: "problem with adobe-flash plugin ubuntu 10.04"
date: 2010-05-20
forum: General Help
---

### Post by yeayu on 2010-05-20
Hi everybody:
I have just installed my ubuntu 10.04 32bits, before i had 9.10 version and all worked ok.
now, i have installed adobe-flash plugin since sypnatic and each moment that i reboot my laptop the sound in firefox don't work. I've been able to solve reinstalling the plugins ones and again.:confused:
What is it happening?
How can I solve it?
Thankx

---

### Post by silkworm2.5 on 2010-05-20
Go into the software center and search 'Ubuntu restricted extras' and install that package then try again.

---

### Post by yeayu on 2010-05-21
it didn't work..
i've been trying a lot of things, several install methods but..don't work anything.
it's only the sound, because i can watch the videos

---

### Post by philinux on 2010-05-21
Open a terminal, apps>access

```
sudo updatedb

then 

locate libflashplayer.so
```

Post back what the locate finds.

---

### Post by tommcd on 2010-05-21
> **yeayu said:**
> 
I have just installed my ubuntu 10.04 32bits, before i had 9.10 version and all worked ok.
So this is a *clean install* of Ubuntu 10.04, as opposed to a *dist-upgrade* from 9.10? Is that correct?
> **yeayu said:**
> 
now, i have installed adobe-flash plugin since sypnatic and each moment that i reboot my laptop the sound in firefox don't work. I've been able to solve reinstalling the plugins ones and again.:confused:
What is it happening?
How can I solve it?
Thankx
Just to rule out a corrupt firefox profile, try launching firefox with a new profile. Rename the .mozilla directory in your home directory to .mozilla.bak. Then restart firefox and see if the sound is fixed.
Is it just the sound in Adobe Flash that has no sound? Or is it all the plugins that have no sound at all?
Try listening to these podcasts from firefox:
[http://www.tuxradar.com/files/podcast/podcast_mp3.rss](http://www.tuxradar.com/files/podcast/podcast_mp3.rss)
Don't download them, just click on the mp3 files and see if you can listen to them with the 
Totem-mozilla plugin, or whatever plugin you are using.
How many firefox addons (extensions) are you using? Perhaps try disabling your addons temporarily and see if the problem goes away. Using a fresh new profile should take care of that, but check to make sure that the addons are disabled.

---

### Post by yeayu on 2010-05-21
> **philinux said:**
> Open a terminal, apps>access

```
sudo updatedb

then 

locate libflashplayer.so
```Post back what the locate finds.

here you have:
```

yeayu@xx-laptop:~$ locate libflashplayer.so
/home/yeayu/.mozilla/plugins/libflashplayer.so
/opt/flex/Player/linux/install_flash_player_9_linux/libflashplayer.so
/opt/flex/sdks/3.0.0/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

```

---

### Post by yeayu on 2010-05-21
> 
Just to rule out a corrupt firefox profile, try launching firefox with a  new profile. Rename the .mozilla directory in your home directory to  .mozilla.bak. Then restart firefox and see if the sound is fixed.


It's fixed, thankx :D

---

### Post by sandyd on 2010-05-21
> **yeayu said:**
> here you have:
```

yeayu@xx-laptop:~$ locate libflashplayer.so
/home/yeayu/.mozilla/plugins/libflashplayer.so
/opt/flex/Player/linux/install_flash_player_9_linux/libflashplayer.so
/opt/flex/sdks/3.0.0/runtimes/air/linux/Adobe AIR/Versions/1.0/Resources/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

```

you got two flashplugins installed. run ```
rm /home/yeayu/.mozilla/plugins/libflashplayer.so
```

---

### Post by tommcd on 2010-05-22
> **yeayu said:**
> It's fixed, thankx :D
Glad it is fixed.
However, you need to understand that, as Carlee said, you have *two flashplugins installed*. This is a problem that you somehow managed to cause yourself.
The reason renaming ~/.mozilla to ~/.mozilla.bak fixed the problem is because that removed one of the flash plugins that you managed to install from your firefox profile.

In the future, only install *one* flash plugin, and you will be just fine. A simple:
```
sudo apt-get install flashplugin-installer
```
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)
will do the trick.

---

### Post by telescopic on 2010-12-03
Thank you for the solution as I ran into the same trouble. I apt-get remove the flash installer for cleaning and also remove the Gnash plugin came with firefox and apt-get install again the flash installer.

New to Ubuntu, I want to know by curiosity, why there is 3 such files in different directories? 2 different npwrapper.libflashplayer.so files resides in different places.

elvin@elvin-laptop:~$ locate libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

------------

Also, I want to ask why there are more than 1 firefox directories. Are 2) and 3) redundant and can be deleted? (see below)

1)It seems firefox really resides in /usr/lib/firefox-3.6.12 , since there is a lot of files there.


2)inside /usr/lib/firefox  , there is
elvin@elvin-laptop:/usr/lib$ cd firefox
elvin@elvin-laptop:/usr/lib/firefox$ ls
plugins

elvin@elvin-laptop:/usr/lib/firefox/plugins$ ls
flashplugin-alternative.so



3)inside  /usr/lib/mozilla   ,there is 

elvin@elvin-laptop:/usr/lib/mozilla$ ls
extensions  plugins
elvin@elvin-laptop:/usr/lib/mozilla$ cd plugins
elvin@elvin-laptop:/usr/lib/mozilla/plugins$ ls
flashplugin-alternative.so  libtotem-cone-plugin.so  libtotem-mully-plugin.so
libflashplayer.so           libtotem-gmp-plugin.so   libtotem-narrowspace-plugin.so

-------------------
Thank you

---

### Post by tommcd on 2010-12-05
> **telescopic said:**
> 
New to Ubuntu, I want to know by curiosity, why there is 3 such files in different directories? 2 different npwrapper.libflashplayer.so files resides in different places.

Also, I want to ask why there are more than 1 firefox directories. Are 2) and 3) redundant and can be deleted? (see below)

1)It seems firefox really resides in /usr/lib/firefox-3.6.12 , since there is a lot of files there.

In theory you could delete /usr/lib/firefox/ and /usr/lib/mozilla/. I would not delete them though.
The stuff in /usr/lib/firefox-3.6.12/ will be replaced when a new version of Firefox comes in from the Ubuntu repos.
The stuff in /usr/lib/firefox/ and /usr/lib/mozilla/ will persist when new versions are Firefox are installed.

For what it is worth, the only place you really need to have *libflashplayer.so* installed to is the: /usr/lib/mozilla/plugins/ directory. I always install the Flash from adobe.com. I just untar the Flash installer .tar.gz file and move *libflashplayer.so* to the /usr/lib/mozilla/plugins/ directory. Then restart Firefox and you are good to go.

---

