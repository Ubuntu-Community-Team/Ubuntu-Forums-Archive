---
title: "Pulseaudio broken/maybe not configured."
date: 2010-09-02
forum: General Help
---

### Post by wanderingarticfox on 2010-09-02
I have this posted on Launchpad too but might have it in the wrong place because I am not getting a response after 48 hours. The following is the most recent trouble I am encountering.[lauchpad 123530]

Been gone a while. I just tried the solution from 1/31/2010 and after running in terminal everything from configure -a to apt-get upgrade this is what I have now showing.
Setting up pulseaudio (1:0.9.19-0ubuntu4.1) ...
update-rc.d: warning: /etc/init.d/pulseaudio missing LSB information

nvoke-rc.d: initscript pulseaudio, action "start" failed.
dpkg: error processing pulseaudio (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)

I do not know enough to know what to do now. Please help.

I have tried a few things now and have more data to report.
Under the Applications folder-->Ubuntu Software-->Installed Software my system shows the following as installed:
Pulse Audio Device Chooser -------------------------->
   " " Manager ----------------------------------->
   " " Preferences -------------------------------> When I try to remove I am informed the Package is not installed
   " " Vol. Control --------------------------------> 'no need for removal'
   " " Vol. Meter Capture and Playback ----->
Under Application --> sound and video I only show icons for:
  Brasero Burner
  K3b
  Movieplayer
  Rhythmbox music player
  Sound Recorder

I have no idea what is wrong other that I most likely messed up when setting up the system. I have no clue what to do since the Pulse Audio shows up as installed but when I try to remove so I can reinstall I am told it is not there. Please help

 Today when I ran update mgr these two lines were at the bottom:
pulseaudio-module-gconf
pulseaudio-module-zeroconfig
I have run through sudo commands a  few times as listed here; dpkg --configure -a ; apt-get -f install ; apt-get --fix-missing instal ; apt-get autoclean ; apt-get autoremove ; apt-get apt-get update folloed by upgrade
Refer to luaunch pad #99388

---

### Post by wanderingarticfox on 2011-02-21
It does not really matter the how or why, but if anyone does something dumb with Rhythmbox like I did [which was remove it] then you can fix it by doing a clean install; just be sure to store all of you files, folders etc. on removable media so you can plug it all back in. I even used a USB jump drive to save my Bookmarks from Firefox.
This, my issue is now solved.:-\"

---

