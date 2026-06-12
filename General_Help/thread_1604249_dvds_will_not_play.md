---
title: "dvds will not play"
date: 2010-10-23
forum: General Help
---

### Post by mambo801 on 2010-10-23
hello

i'm running ubuntu 9.10 and windows xp. orginally my drives worked fine on both OS's but now on ubuntu i cannot play dvds.

i can open all disks (data, and dvd movies) and retrieve/copy files from both. both types of disks are picked up by ubuntu and are displayed as normal.

i just can't play movies. i use to only use Movie Player but then i started having this problem and so i thought i'd install VLC media player, hoping this would fix the problem or at least work on its own. didn't help though.

Both VLC and Media Player start but don't play. Media Player opens then closes. VLC opens you see it try and pick up the disk then drops the disk info and does nothing.

I have started up windows xp and used VLC to watch movies and everything works fine so it shouldn't be the drives themselves. i'm guessing its an update which has caused the problem.

i'm not a strong linux user (although i love ubuntu) and i need help to sort this one out.

i know there are commands which will give out info of whats happening and that sort of thing but thats where my tech smarts ends. so if someone could please run me through the process i'd much appreciate it!

cheers

---

### Post by GlazedWicker on 2010-10-23
You need to install some packages in order to play commercially encrypted dvds.

```
 sudo apt-get install libdvdread4
```


```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by efflandt on 2010-10-23
I never could get Media Player (Totum) to work properly in 9.10.  Depending upon which gstreamer modules were installed, either I could not access DVD menus, or I had no sound.  But vlc worked fine.

Normally you would install ubuntu-restricted-extras, and read the description there about what you also need to play DVD's (the libdvdread thing mentioned above).

When I recently upgraded a system from 9.10 to 10.04, flash appeared to be still installed, but would not work and did not show in Firefox Add-ons, and ubuntu-restricted-extras showed as not installed.  Flash still did not show up after installing ubuntu-restricted-extras (which includes it), so I had to mark flashplugin-intstaller for Reinstallation.

---

### Post by perspectoff on 2010-10-23
* You can install libdvdcss2 as a 64-bit .deb package without installing the Medibuntu repositories: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

    or a 32-bit .deb package: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb


for more info see:

[http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability)

or

[http://kubuntuguide.org/All#DVD_Playback_Capability](http://kubuntuguide.org/All#DVD_Playback_Capability)

as well as ubuntu-restricted-extras

---

### Post by luisito on 2010-10-23
Maybe so. However, it may be a better idea to install libdvdcss2 INSTALLING the medibuntu repository.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mambo801 on 2010-10-24
> **efflandt said:**
> I never could get Media Player (Totum) to work properly in 9.10.  Depending upon which gstreamer modules were installed, either I could not access DVD menus, or I had no sound.  But vlc worked fine.

Normally you would install ubuntu-restricted-extras, and read the description there about what you also need to play DVD's (the libdvdread thing mentioned above).

When I recently upgraded a system from 9.10 to 10.04, flash appeared to be still installed, but would not work and did not show in Firefox Add-ons, and ubuntu-restricted-extras showed as not installed.  Flash still did not show up after installing ubuntu-restricted-extras (which includes it), so I had to mark flashplugin-intstaller for Reinstallation.

> **perspectoff said:**
> * You can install libdvdcss2 as a 64-bit .deb package without installing the Medibuntu repositories: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb

    or a 32-bit .deb package: 

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb


for more info see:

[http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:All#DVD_Playback_Capability)

or

[http://kubuntuguide.org/All#DVD_Playback_Capability](http://kubuntuguide.org/All#DVD_Playback_Capability)

as well as ubuntu-restricted-extras

[COLOR=DarkGreen][FONT=Arial Black]Hey guys thanks for all of your suggestions! i tried installing all the lib packages but still didn't work. and i had the restricted package already installed aswell.

so i tried the only other suggestion that might fix it.....mark Mplayer and VLC and all associated packages for re-installation. and bingo its fixed. now my son can get of my back!!! he's 4.

so thanks guys 4 your help!!

cheers mambo
[/FONT][/COLOR]

---

