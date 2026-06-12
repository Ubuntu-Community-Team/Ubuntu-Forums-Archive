---
title: "trouble installing non-free codecs"
date: 2006-04-27
forum: General Help
---

### Post by threethirty on 2006-04-27
Now I've done this many times and never had this happen before.  I have all the repositories enabled, but i still cant get this to work.

this is the guide I'm using [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) and this is my output
```
three@CondorV2:~$ sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-plugins-multiverse
three@CondorV2:~$
```

any ideas:-k

---

### Post by jazzmuzik on 2006-04-27
the "-multiverse" part doesn't look right.

---

### Post by threethirty on 2006-04-27
what exactly doesnt look right i copied and pasted from the website

i tried to use easyubuntu before this could that be causing the problem?

---

### Post by mjm115 on 2006-04-27
What does

> 
apt-cache search gstreamer


give you?  I think gstreamer0.8 is upgraded to something else in the repository.  I could be wrong though.  I'm not sitting in front of my Kubuntu box.  My job is still on Windows :-| :cry:

---

### Post by minhaz4u on 2006-04-27
I would suggest you to use Automatix...It's the most stable answer for your prob ;) 

Automatix is available only for Ubuntu/Kubuntu/Xubuntu Breezy x86 (NO support for ppc and AMD64 packages) and its changelog is available here.

Please scroll down for installation instructions of Automatix.

Important Note: Please DO NOT run synaptic while running automatix

Please DO NOT click on update-notifier if it appears while running automatix.

Please note: To remove softwares installed by automatix, visit the following thread:
[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

If u are behind a proxy and cannot get automatix to work read this post

Automatix updated to version 5.8.1
New features in version 5.8.1:
a) bug in firefox 1.5.0.2 installation fixed

Introduction:

This is a graphical interface for installation of a lot of apps on Ubuntu/Kubuntu/Xubuntu BREEZY (DOES NOT WORK ON Warty, Hoary or Dapper) and for tweaking a few things to get your Ubuntu box up and working in full throttle in the quickest possible timespan.

Features:
a) Shoots up xterm for full debug info (giving you a good idea about the status of your download , changes being made to your system, etc)
b) deletes all downloaded files (except those downloaded by apt-get) automatically after installation.
c) automatix does not overwrite anything without making a date_and_time_based backup.
d) When u install a new version of automatix, it automatically uninstalls and replaces the last version.
e) Automatix will refuse to run if user has synaptic/update-manager/apt-get/dpkg running and will exit gracefully.
f) Automatix will give the user the option to restore his/her original sources.list after finishing all installations.

Please note: Options 38 to 46 require manual intervention and clicking and hence have been taken to the end. The first 32 options install without any user input (if u choose to install them).

Capabilities:
1) Installs multimedia codecs
2) Installs all Firefox plugins (java, flash, etc) (except Adobe reader and mplayer)
3) Installs RAR, ACE and UNRAR archive support
4) Installs skype
5) Installs Acrobat reader 7 and firefox plugin for the same.
6) Installs Gnomebaker (CD/DVD burning s/w for GNOME)
7) Installs gftp (FTP client for GNOME with ssh capability)
8) Installs Amule (File sharing program)
9) Installs Frostwire (GPL clone of Limewire)
10) Installs multimedia editors (Audacity (audio), Kino (video), EasyTag (ID3))
11) Installs DVD (dvdrip) ripper
12) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
13) Installs totem-xine, Realplayer, VLC and Beep Media Player (with docklet)
14) Installs Opera Browser
15) Installs Debian Menu (shows all installed applications) (this kills and restarts your gnome-panel without warning u but its a completely harmless operation!)
16) Installs Bittornado and Azureus (Bittorrent clients)
17) Installs Avidemux (Video editing tool) (New version 2.1.0)
18) Enables Numlock on (turns numlock on Gnome startup)
19) Installs Programming Tools (Anjuta (C/C++ IDE), Bluefish (HTML editor) and Screem (Web Development Env.))
20) Install GnomePPP (Graphical Dial up connection tool)
21) Installs MS true type fonts
22) Configures ctrl-alt-del to start gnome-system-monitor (aka windows)
23) Installs Streamripper and Streamtuner
24) Installs NON-FREE audio and dvd codecs
25) Installs ndisgtk (WiFi configurator Graphical user interface)
26) Upgrades Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer.
27) Adds 3 nautilus scripts (open any file with gedit as root; open a nautilus window as root in any folder; open gnome search tool in any folder (Right click in a nautilus window and look under "scripts")
28) Installs SUN'S JAVA JRE version 1.5
29) Installs SUN'S JAVA JDK version 1.5
30) Installs wine (u need to run winecfg manually after installation)
31) Enables ejection of CD when CDROM drive button is pressed.
32) Installs AMSN 0.95 (MSN client with webcam support)
33) Installs Mercury Messenger (Java based MSN client with webcam support)
34) Installs BUM (Boot-up Manager)
35) Installs DCPP (Linux DC++ client)
36) Installs sbackup (Backup and restoration solution)
37) Installs Listen Music manager (with repository)
38*) Installs firestarter (GNOME firewall frontend) and adds firestarter to GNOME startup
39*) installs gdesklets (GNOME eyecandy) and adds gdesklets to GNOME startup
40*) Gamepads (Makes USB gamepads work)
41*) Turns DMA ON on Intel and AMD machines (needs a restart)
42*) NVIDIA cards (Detects Nvidia cards and installs drivers) (Needs a restart)
43*) Adds midi capability to your Ubuntu box (test by playing a midi file with timidity or pmidi from terminal)
44*) Installs Firefox 1.5.0.2 and its plugins(themes and extensions are not retained, bookmarks need to be copied from backup folder)
45*) Installs Mozilla-Thunderbird 1.5 (US-only version) (no support for non-US-english language packs and enigmail)
46*) Fixes Gnome sound related issues (ALSA and ESD config) (needs a restart) (ONLY FOR GNOME! NOT TO BE USED ON KDE/XFCE)

* --> These options require manual intervention and clicking. Please stand by!

PLEASE DO NOT INSTALL (24) IF YOU ARE IN THE UNITED STATES OF AMERICA. IT IS ILLEGAL TO DO SO.

Installation Instructions:

To install Automatix in Ubuntu do the following from terminal(one line at a time, pressing enter after each step):
```
wget http://beerorkid.com/automatix/automatix_5.8-1_i386.deb
sudo dpkg -i automatix_5.8-1_i386.deb
```

To install Automatix in Kubuntu/Xubuntu refer to the following thread:
[http://ubuntuforums.org/showthread.php?t=151387](http://ubuntuforums.org/showthread.php?t=151387)

Automatix gets installed in Applications--> System Tools (GNOME)
and in main menu-->System (KDE/XFCE)

To run Automatix from terminal simply do:
```
Automatix
```

---

### Post by threethirty on 2006-04-27
```
three@CondorV2:~$  apt-cache search gstreamer
gnome-media - The GNOME Media Utilities
gstreamer0.8-aa - AA-lib plugin for GStreamer
gstreamer0.8-alsa - ALSA plugin for GStreamer
gstreamer0.8-artsd - aRtsd plugin for GStreamer
gstreamer0.8-audiofile - AudioFile plugin for GStreamer
gstreamer0.8-caca - Colour AsCii Art library plugin for GStreamer
gstreamer0.8-cdparanoia - cdparanoia plugin for GStreamer
gstreamer0.8-doc - GStreamer documentation
gstreamer0.8-dv - DV plugin for GStreamer
gstreamer0.8-dvd - DVD plugin for GStreamer
gstreamer0.8-esd - Enlightened Sound Daemon plugin for GStreamer
gstreamer0.8-festival - Festival speech synthesis plugin for GStreamer
gstreamer0.8-flac - FLAC plugin for GStreamer
gstreamer0.8-gnomevfs - Gnome VFS plugin for GStreamer
gstreamer0.8-gsm - GSM plugin for GStreamer
gstreamer0.8-hermes - colorspace conversion plugin for GStreamer based on hermesgstreamer0.8-jack - JACK plugin for GStreamer
gstreamer0.8-jpeg - JPEG plugin for GStreamer
gstreamer0.8-mikmod - MikMod decoder plugin for GStreamer
gstreamer0.8-misc - Collection of various GStreamer plugins
gstreamer0.8-musepack - Musepack (MPC) audio decoder plugin for GStreamer
gstreamer0.8-oss - OSS plugin for GStreamer
gstreamer0.8-plugin-apps - Simple GStreamer applications
gstreamer0.8-sdl - SDL videosink plugin for GStreamer
gstreamer0.8-sid - C64 SID decoder plugin for GStreamer
gstreamer0.8-speex - Speex plugin for GStreamer
gstreamer0.8-theora - Theora plugin for GStreamer
gstreamer0.8-tools - Tools for use with GStreamer
gstreamer0.8-vorbis - Vorbis plugin for GStreamer
gstreamer0.8-x - X videosink plugin for GStreamer
juk - music organizer and player for KDE
libglib-cil - CLI binding for the GLib utility library
libgstreamer-gconf0.8-0 - GConf support for GStreamer
libgstreamer-gconf0.8-dev - Development files for GConf support for GStreamer
libgstreamer-plugins0.8-0 - Various GStreamer libraries and library plugins
libgstreamer-plugins0.8-dev - Development files for various GStreamer library and library plugins
libgstreamer0.8-0 - Core GStreamer libraries, plugins, and utilities
libgstreamer0.8-dev - GStreamer development libraries and headers
python-gst - generic media-playing framework (Python bindings)
goobox - CD player and ripper for GNOME
gstreamer-editor - GStreamer Pipeline Editor and other GUI tools
gstreamer0.8-a52dec - ATSC A/52 audio decoder plugin for GStreamer
gstreamer0.8-cdio - low-level CD-ROM reading and control plugin for GStreamer
gstreamer0.8-ffmpeg - FFmpeg plugin for GStreamer
gstreamer0.8-gtk - GdkPixbuf decoder plugin for GStreamer
gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer
gstreamer0.8-mms - mms plugin for GStreamer
gstreamer0.8-mpeg2dec - MPEG1 and MPEG2 video decoder plugin for GStreamer
gstreamer0.8-pitfdll - DLL/QTX loader plugin for GStreamer
gstreamer0.8-plugins - All GStreamer plugins
gstreamer0.8-swfdec - SWF (Macromedia Flash) decoder plugin for GStreamer
libglib2.0-cil - CLI binding for the GLib utility library 2.0, unstable version
libgstreamer0.8-ruby - GStreamer 0.8 bindings for the Ruby language
libgtksourceview1-ruby - GTKSourceView bindings for the Ruby language
soundconverter - simple sound converter application for GNOME
swf-player - SWF (Macromedia Flash) player
tap-plugins - Tom's Audio Processing LADSPA plugins
thoggen - DVD backup utility based on GStreamer and Gtk+
amarok - versatile and easy to use audio player for KDE
amarok-gstreamer - GStreamer engine for the amaroK audio player
kaffeine-gstreamer - GStreamer engine for kaffeine media player
serpentine - an application for mastering audio CD
totem-gstreamer - A simple media player for the Gnome desktop based on gstreamertotem-gstreamer-firefox-plugin - Totem Firefox Plugin - gstreamer version
three@CondorV2:~$


```

---

### Post by mjm115 on 2006-04-27
There is no 'gstreamer0.8-plugins-multiverse' in this list.  That's why you get the error message.  Perhaps you meant to type:

> 
apt-get install gstreamer0.8-plugins


I see that listed.

---

### Post by Jagot on 2006-04-27
The package in question, gstreamer0.8-plugins-multiverse, does exist - I have it.  It's the only one from the multiverse repository as far as I can see that you attempted to install there.  Are you absolutely sure you have the multiverse repository enabled?

You may want to check this out and go through the gui method to check:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by threethirty on 2006-04-27
i have all of the repositories selescted and i ran Automatix and now i cant open firefox (i click the icon and the window border opens and the closes)  and i/it broke some of the packages (that i had to unsitall because they couldnt be fixed)

im trying to install firefox 1.5 again](*,)

---

### Post by jazzmuzik on 2006-04-27
Ah, you are correct, gstreamer0.8-plugins-multiverse does exist. I saw the multiverse and thought that was part of the text for which repository to enable.

Anyway, I'm on Breezy and it installed for me.

Not sure what the problem could be in your case.

---

### Post by threethirty on 2006-04-28
ok i tried to reinstall firefox (with automatix) and now its been installing for 11 hours 

i have epiphany installed is there any way to get flash working in it

---

### Post by jazzmuzik on 2006-04-28
Look in Synaptic, search on 'flash' and you find a flashplayer-mozilla plugin. Install that.

---

### Post by threethirty on 2006-04-28
thanks jazz that worked

---

