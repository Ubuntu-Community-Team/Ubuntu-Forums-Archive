---
title: "Flash videos keep crashing :("
date: 2010-12-26
forum: General Help
---

### Post by bumder on 2010-12-26
Is it normal for the flash player in Ubuntu 10.04 to be quite slow, and unreliable? I know I'm only on a Samsung nc10 netbook, but that should be enough oompff.

Seems if I have youtube open in two windows (chrome or firefox, same issue), and then close one of the windows, it crashes all flash videos. Sometimes it will even crash on its own :(

Any ideas?
Thanks

Here are my current plugins:

Default Plug-in - Version: 1
Provides functionality for installing third-party plug-ins

Shockwave Flash (2 files)
Shockwave Flash 10.1 r103

Java(TM) Plug-in 1.6.0_22
The next generation Java plug-in for Mozilla browsers.

Chrome PDF Viewer
Portable Document Format

VLC Multimedia Plugin (compatible Totem 2.30.2)
The Totem 2.30.2 plugin handles video and audio streams.

Windows Media Player Plug-in 10 (compatible; Totem)
The Totem 2.30.2 plugin handles video and audio streams.

DivX® Web Player
DivX Web Player version 1.4.0.233

QuickTime Plug-in 7.6.6
The Totem 2.30.2 plugin handles video and audio streams.

---

### Post by fatal_ERROR777 on 2010-12-26
I think I had the same problem. I had the same buggy flash player. Uninstall the laggy version and install the trusted verison of it at the original [site]("http://get.adobe.com/flashplayer/?no_redirect"). 
  Also, you need to check the temperature of your laptop. If your laptop is hotter than 50 degrees celsius, buy a cooling system.
It may look like this:
[img]http://www.notebooklist.net/files/imagecache/fullsize/files/41I-vRtvnCL__SS500_.jpg [/img]

---

### Post by bumder on 2010-12-26
Hey, thanks for the reply!

Will look at uninstalling and letting the adobe website install itself like you said. It was updated using [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu)

What is the cleanest way to remove flash? Through package manager, or with terminal and a purge command?

Thanks

---

### Post by fatal_ERROR777 on 2010-12-26
The best way to remove programs for newbies is to remove them by pacage manager. Advanced users should use command-line, because if there was any problem detected, command-line will display the output of it.

---

### Post by bumder on 2010-12-26
A search for 'flash' in package manager shows two things install:

flashplugin-installer and ubuntu-restricted-extras

So if I mark flashplugin-installer for removal, that should safely remove flash player from my system, then I can reinstall direct from Adobe's site?

Thanks

---

### Post by Sylos on 2010-12-26
If you use mozilla firefox there is an add on that will set it up for you (remove andy conflicts and install the correct one).

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

I dont know about your hardwade - so the following is just an anicdotal bit of observation:

I recently had problems with flash on a intel celery 2.6g processor and found out that there are issues with coping with flash in linux. Apparently the linux flash player does not support hardware decoding for flash player so the entire load is taken by the CPU - quite stressful for old or underpowered machines. Doing all the decoding takes a lot of cpu cycles and, in my case, made all flash videos jumpy and laggy. I tried a number of solutions and didnt get anywhere - in the end I changed the MB and CPU for an old AMD I had lying around.

If your having trouble with lagging/jumping you can try the flash aid add on and make sure everything is ok there and then (if it persists) try disabling the GPU validation (see Below) - this did have a positive effect for me but it isnt life changing.

[http://www.webgapps.org/flash/optimization](http://www.webgapps.org/flash/optimization)

Good luck.

---

### Post by fatal_ERROR777 on 2010-12-26
> **bumder said:**
> 
So if I mark flashplugin-installer for removal, that should safely remove flash player from my system, then I can reinstall direct from Adobe's site?

Thanks
Yes, do it please. If this doesn't work, I'm lost, because I'm still learning programming languages.

---

### Post by Sylos on 2010-12-26
I dont think removing the flashplugin-installer package will purge flash as this appears to only be the installer for acquiring the relevant plugins from adobe. I would strongly recomend trying the flashAid add on to do this for you.

If you really want to do it yourself I think you'll need to use the following:

```
sudo apt-get remove flashplugin-nonfree
```

Assuming the above command is successful you will then be able to download the .deb from adobe and install it. But I really have to recomend using the addon script to ensure you dont compound matters.

---

### Post by bumder on 2010-12-26
Will give that Flash Aid a try. Hopefully it will sort out Google Chrome too, as they should use the same flash libraries.

Cheers

EDIT: Going to have to wait till the new year now, as my ISP says I've hit my 10Gb limit this month!!
Will let you know the outcome in a few days then.

---

### Post by bumder on 2010-12-28
If using Flash Aid, how do you keep flash player up to date with latest version? Do you update through Flash Aid, or use a separate PPA?

Thanks.

---

### Post by bumder on 2010-12-30
UPDATE: Tried the latest Flash Aid 2 Add-on for Firefox, still waiting to see if it has remedied my flash woes.

When using Flash Aid, you may have to place the icon on your nav bar manually, as I did. Info on [http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid) under 'installation'

---

### Post by fatal_ERROR777 on 2011-01-15
oh sorry for confusing you, I installed flash player directly from adobe website without removing anything. Maybe Flash aid will work for you, maybe not. Also Ubuntu has quite poor driver support for Intel

---

### Post by mipesom on 2011-02-06
Had the same problem. But it's easy to solve (after figuring out what it caused and THAT took days!). Disable VLC-plugin and the trouble is gone. :)

---

