---
title: "Default CD Player - Autostart"
date: 2006-04-21
forum: General Help
---

### Post by SteveF on 2006-04-21
I know this should be simple, but I just can't find a way to do it.  When I put an audio CD in my CD Drive, ksCD starts up automatically.  I'd prefer to start a different app (or possibly no app - haven't decided yet).

I tried searching the ofrums, but the only mention I saw was to go to peripherals (or devices)->media->audio CD.  I don't see that path or anything similar to it.

Any ideas on how to do this?

Thanks,

Steve

---

### Post by gingermark on 2006-04-22
Press Alt+F2 and type ```
kdesu kate /etc/ivman/IvmConfigActions.xml
```
This file controls automounting and autoplaying. You can "comment out" sections by inserting '<!--' at the beginning of the section you would like to block and '-->' at the end.

So, if you wanted to block KsCD from playing, find the following section (should start at line 107:
```
<!-- open kscd for audiocds -->
   <ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match>
```
and change it to:
```
<!-- open kscd for audiocds -->
  <!-- <ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match> -->
```

As far as using a different program, I guess you could edit that section changing the '/usr/bin/kscd' part to point to another program, but I don't know enough about how the file works to say for certain.

Apparently this will have a GUI interface when Dapper is released.

---

### Post by Rog131 on 2006-04-22
In KDE 3.5.2   K > System Settings > Storege Media -> Medium types:Audio CD

You can choose what happens when system notices new media (cd/dvd/what ever)

Notifications:

Open in New window
Extract and Encode Audio Tracks
Play
Play Audio CD with Kaffeine **(You can put in your favorite)**
.
.
.
Do Nothing

Advanced:
Enable HAL backend
Enable CD polling
Enable medium application autostart after mount ** (NOTE !!)**

---

### Post by SteveF on 2006-04-22
[QUOTE=gingermark]Press Alt+F2 and type ```
kdesu kate /etc/ivman/IvmConfigActions.xml
```
This file controls automounting and autoplaying. You can "comment out" sections by inserting '<!--' at the beginning of the section you would like to block and '-->' at the end.

So, if you wanted to block KsCD from playing, find the following section (should start at line 107:
```
<!-- open kscd for audiocds -->
   <ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match>
```
and change it to:
```
<!-- open kscd for audiocds -->
  <!-- <ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match> -->
```

As far as using a different program, I guess you could edit that section changing the '/usr/bin/kscd' part to point to another program, but I don't know enough about how the file works to say for certain.

Apparently this will have a GUI interface when Dapper is released.[/QUOTE]


Thanks.  I can live with the manual change.  But, I'd prefer an interface to do these mods (gets to be a pain remembering where all the changes are).  But if Dapper will be getting it, good enough.

Steve

---

### Post by SteveF on 2006-04-22
[QUOTE=Rog131]In KDE 3.5.2   K > System Settings > Storege Media -> Medium types:Audio CD

You can choose what happens when system notices new media (cd/dvd/what ever)

Notifications:

Open in New window
Extract and Encode Audio Tracks
Play
Play Audio CD with Kaffeine **(You can put in your favorite)**
.
.
.
Do Nothing

Advanced:
Enable HAL backend
Enable CD polling
Enable medium application autostart after mount ** (NOTE !!)**[/QUOTE]


I'm running Kubuntu for Breezy Badger.  I'm not sure of the KDE version that comes with it (along with whatever updates Adpet informs me about), but I don't see Storage Media under System Settings.

Steve

---

### Post by gingermark on 2006-04-22
To upgrade to KDE 3.5.2 add the following repositories to your sources.list located in /etc/apt:

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main
deb [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main

Save the file and then do:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Rog131 on 2006-04-22
KDE version: Konqueror (or System Settings...) > Help > About KDE ->Tells that this is K Desktop Enviroment. Release 3.5.2 (or your release).

Info about upgrades (HowTo and Where):
[http://www.kubuntu.org/](http://www.kubuntu.org/)
- KOffice 1.5 Released with Kubuntu Packages
- KDE 3.5.2 Released with Kubuntu Packages
- Amarok 1.3.8 Released with Kubuntu Packages

***NOTE***
There has been troubles with upgrade to KDE 3.5.2.

KDE 3.5.2 problems and solutions:
1. KDE 3.5.2 power management
[http://kubuntuforums.net/forums/index.php?topic=4373.0](http://kubuntuforums.net/forums/index.php?topic=4373.0)
2.Konsole not configurable
[http://www.ubuntuforums.org/showthread.php?t=154417](http://www.ubuntuforums.org/showthread.php?t=154417)
3.Topic: Konqueror 2 x Search Engine Box
[http://kubuntuforums.net/forums/index.php?topic=4305.0](http://kubuntuforums.net/forums/index.php?topic=4305.0)

---

