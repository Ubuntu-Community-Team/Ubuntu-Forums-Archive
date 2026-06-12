---
title: "[solved] - HowTo setup your NB100"
date: 2010-01-05
forum: General Help
---

### Post by Tuliku on 2010-01-05
[COLOR="DarkRed"]Hi, after many times testing and trying out things, i thought i'd share my experience with you.

The info below is collected from several different topics throughout this forum and other places on the internet.
Credit goes to all people who helped and shared their info.

**So, my Toshiba NB100 setup is as following:**
2 GB ram (original 1 gb, changed it myself)
320 GB harddisk (original 120 gb, changed it myself)
- 1 GB /boot
- 25 GB /
- 3 GB swap
- 290 GB /home

I have mentioned every where which user provided what info, and also the source page, but to save you the time form digging through the pages, i have summarized the necessary info as well.
[/COLOR]

[COLOR="Blue"]**Installing**[/COLOR]
Download Ubuntu
--->  [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
Create bootable flash drive
--->  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

After installation start synaptic package manager and press "Mark all available upgrades", and then press "Apply".
When done, restart.

[COLOR="Blue"]**Additional software**[/COLOR]
Additional software installed through Synaptic Package Manager:
(you might not find it useful or want to use different software)
- audacity
- audacious
- gparted
- thunderbird
- ntfsprogs
- conky
- lm-sensors
- hddtemp
- acroread
- adobe-flashplugin
- gimp
- all g-streamer plugins
- pidgin
- mplayer
- stunnel4
- vlc
- java6
- gedit-plugins

[COLOR="Blue"]**Normal desktop in UNR**[/COLOR]
Thanks to user [COLOR="DarkOrchid"]**quiricada**[/COLOR]
In unr mode:
System -> Preference -> Startup applications
uncheck -> maximus
uncheck -> netbook launcher

On the top panel
Right click the little ubuntu logo (it's the go home applet) and remove it.
Then right click on any part of the blank portion of the top panel.
Select add to panel
Select main menu (the main gnome menu)
Then i move this to the leftmost part of the panel

Note:
Some part of the top panel may look blank but it is actually the window list.
If you right click and you don't get the "add to panel" selection item, you are right clicking on the window list.
If you can't right click and get the "add to panel" selection item, just:
**1.** Remove the window list,
**2.** Add main menu,
**3.** Add back the window list)
Restart

[COLOR="Blue"]**Enable rightclick**[/COLOR]
Thanks to user: [COLOR="Purple"]**mbeierl**[/COLOR]
Start in a terminal: gconf-editor
Apps -> Nautilus -> Preferences 
- Enable -> Show Desktop
Apps -> Nautilus -> Desktop
- Enable the icons that you want, otherwise the desktop stays blank

[COLOR="Blue"]**Removing unnecessary applications from starting up**[/COLOR]
System -> Preferences -> Startup Applications
Uncheck:
- check for new hardware drivers
- Evolution Alarm Notifier
- Print Queue Applet
- User Folder Update
- Visual Assistance

[COLOR="Blue"]**Audacious skins**[/COLOR]
If you use Audacious as your music player, and want some different skin, check these links:
--->  [http://www.customize.org/list/winamp2](http://www.customize.org/list/winamp2)
--->  [http://skinz.org/skins.phtml?category=21](http://skinz.org/skins.phtml?category=21)
Copy any skin you download into:
```
~/.local/share/audacious/Skins
```
Then, in audacious, right click the player and go into the preferences to change your skin into the new one.

[COLOR="Blue"]**Winamp presets in Audacious**[/COLOR]
To download the WinAmp presets type:
```
wget http://www.xmms.org/misc/winamp_presets.gz
```
To install the presets for the Audacious media player type:
```
gunzip -c winamp_presets.gz > ~/.config/audacious/eq.preset
```

[COLOR="Blue"]**Facebookchat plugin for Pidgin**[/COLOR]
The standard facebookchat plugin for pidgin 1.60 in synaptic does not work.
Therefore better download the latest on 1.64 from:
---> [http://code.google.com/p/pidgin-facebookchat/downloads/list](http://code.google.com/p/pidgin-facebookchat/downloads/list)

[COLOR="Blue"]**Add the Medibuntu repository**[/COLOR]
```
echo deb http://packages.medibuntu.org/ karmic free non-free | sudo tee -a /etc/apt/sources.list
```
Add the verification key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Now you can add the following codecs for your media players:
- w32 codecs
- non-free-codecs

[COLOR="Blue"]**Installing Skype**[/COLOR]
---> [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)
Download the right one for your system and install (double click on the downloaded file)

[COLOR="Blue"]**Fix the build-in mic**[/COLOR]
---> [http://ubuntuforums.org/showthread.php?t=1339409&page=1](http://ubuntuforums.org/showthread.php?t=1339409&page=1)
**1.** 
From ubuntu menu go to 
System > Administration > Synaptic Package Manager
**2.** 
Install:
- linux-backports-modules-alsa-2.6.31-16-generic
- linux-backports-modules-alsa-karmic
- pulseaudio
- paman
- pavumeter
The version number of this package should match your current (latest) kernel.
To find out your kernel version type in a terminal: uname -a
**3.**
From the ubuntu menu go to 
System > Preferences > Sound > Input Tab
Make sure input sound is not muted and that the volume is on the "unamplified" mark or the sound will be distorted (in case you have previously dragged it to max to fix the mic).
**4.**
Type in a terminal: alsamixer
F3
set all to maximum, and unmute all (pressing m)
F4
set all to maximum, choose one of the options if you are given options (probably built-in or external)
ESC
**5.**
Start Skype
Options -> Sound Devices
Uncheck "Allow Skype..."
Click "Apply"
Make a test sound & test call

[COLOR="Blue"]**Conky**[/COLOR]
Lots of screenshots and scipts:
---> [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+screenshots](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+screenshots)

How to setup basic conky, thanks to user: **[COLOR="DarkOrchid"]Bruce M.[/COLOR]**
---> [http://ubuntuforums.org/showthread.php?p=5436679#post5437628](http://ubuntuforums.org/showthread.php?p=5436679#post5437628)
**1.**
Run hddtemp as regular user in conky
```
sudo dpkg-reconfigure hddtemp
```
"yes" to suid, agree with the rest.
**2.**
Create a directory in /home/<user>/ called /Conky
Save the attached file "conkymain.txt" int this directory
(/home/<user>/Conky/conkymain).
Remove the ".txt" part from the file so it is just "conkymain".
(it was needed for being able to upload the file)
Alternatively you can copy and paste a conky file from one of the posts in the threads above that you like into your conkymain file and save it.
**3.**
Create a hidden file ~/.startconky
```
gedit ~/.startconky
```
- In this empty file paste the following:
```
#!/bin/bash
sleep 0 &&      # 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```
**4.**
Now you must make ~/.startconky executable.
```
chmod a+x ~/.startconky
```
**5.**
Getting Ubuntu to Autostart conky.
- System -> Preferences -> Sessions -> Startup Programs
- Click on the ADD button:
- Name: Conky <<-- anything you want
- Description: <<--- anything you want (mine is blank)
- Command: <<-- see the "Open Icon" click on that. When your home folder shows, right click to show hidden files if not visible ... and find the hidden file: ".startconky". Highlight it and click "OK".
- Close
- Now: [Ctrl]+[Alt]+[Backspace] to restart your session and conky will start in xx seconds, depending on your sleep command.

[COLOR="Blue"]**Usefull links**[/COLOR]
Thanks to user: [COLOR="DarkOrchid"]**wojox**[/COLOR]
Handy advice on how to do some settings and how to get Thunderbird 3 & other stuff.
---> [http://wojox.homelinux.net](http://wojox.homelinux.net)

Thanks to user: [COLOR="DarkOrchid"]**Spaceman9**[/COLOR]
The Perfect Desktop - Ubuntu 9.10 (Karmic Koala) 
---> [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala)
Comprehensive Multimedia & Video Howto 
---> [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Linux software equivalent to Windows software 
---> [http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
Linux replacements for your favorite Windows apps 
---> [http://www.linuxworld.com/news/2008/041108-linux-replacements-for-your-favorite.html](http://www.linuxworld.com/news/2008/041108-linux-replacements-for-your-favorite.html)
Forging Ubuntu 
---> [http://www.howtoforge.org/howtos/linux/ubuntu](http://www.howtoforge.org/howtos/linux/ubuntu)

**Linux compatible Hardware:**
Phoronix 
---> [http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)
Linux Tested 
---> [http://www.linuxtested.com/](http://www.linuxtested.com/)
Hardware Compatibility List 
---> [http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)

**News and Information About Linux and Linux distros:**
Distrowatch 
---> [http://distrowatch.com/](http://distrowatch.com/)
Linux Today 
---> [http://www.linuxtoday.com/](http://www.linuxtoday.com/)
Linux Inside
---> [http://www.linuxinsider.com/](http://www.linuxinsider.com/)
Linux Journal
---> [http://www.linuxjournal.com/](http://www.linuxjournal.com/)
Linux.com
---> [http://www.linux.com/](http://www.linux.com/)

**Ubuntu Guide for All Things Ubuntu:**
Ubuntu 9.10 (Karmic Koala) Guide 
---> [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
2.7 Graphics and Video Applications 
---> [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Graphics_and_Video_Applications](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Graphics_and_Video_Applications)
2.8 Multimedia Applications 
---> [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Multimedia_Applications](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Multimedia_Applications)

---

