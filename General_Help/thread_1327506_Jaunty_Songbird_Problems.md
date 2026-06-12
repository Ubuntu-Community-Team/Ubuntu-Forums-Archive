---
title: "Jaunty Songbird Problems"
date: 2009-11-15
forum: General Help
---

### Post by nmaster on 2009-11-15
Sometimes Songbird just won't play any songs.  If I double click on a song it will just skip to the next one, and the one after that, and the one after that, etc.  I can't figure out when it will happen but it just does sometimes.  

I tried uninstalling and reinstalling, but that didn't fix anything.  Everything was fine until a couple weeks ago, but I can't remember changing anything major.  I thought it might have to do with the kernel update, but using older ones that I never delete doesn't fix anything. 

Has anyone else had any problems?

According to the help drop-down menu this is what I'm using. 

Version: Songbird 1.1.2, Build 1042 (20090331141711)

---

### Post by arnab_das on 2009-11-15
> **neal.m.master said:**
> Sometimes Songbird just won't play any songs.  If I double click on a song it will just skip to the next one, and the one after that, and the one after that, etc.  I can't figure out when it will happen but it just does sometimes.  

I tried uninstalling and reinstalling, but that didn't fix anything.  Everything was fine until a couple weeks ago, but I can't remember changing anything major.  I thought it might have to do with the kernel update, but using older ones that I never delete doesn't fix anything. 

Has anyone else had any problems?

According to the help drop-down menu this is what I'm using. 

Version: Songbird 1.1.2, Build 1042 (20090331141711)

have u installed ubuntu restricted extras?

---

### Post by nmaster on 2009-11-15
yes i do have the restricted extras.  

and just to be clear, songbird works most of the time i can't figure out a pattern to see when i get problems.

---

### Post by arnab_das on 2009-11-15
> **neal.m.master said:**
> yes i do have the restricted extras.  

and just to be clear, songbird works most of the time i can't figure out a pattern to see when i get problems.

hmm.well i guess you could delete the songbird directory (and all the config files) and install it again. and see if the prob goes away.

---

### Post by nmaster on 2009-11-15
From my original post:

> **neal.m.master said:**
> 
I tried uninstalling and reinstalling, but that didn't fix anything. 

---

### Post by arnab_das on 2009-11-15
> **neal.m.master said:**
> From my original post:

okay, how about ```
sudo apt-get purge ubuntu-restricted-extras && sudo apt-get install ubuntu-restricted-extras
```no harm in trying.
btw did u delete the configuration files when u removed songbird?

---

### Post by nmaster on 2009-11-15
since i installed from a *.deb, i did this:

sudo dpkg --purge songbird

according to the man page that should have deleted all of the configuration file.

---

### Post by nmaster on 2009-11-15
also, reinstalling the restricted-extras didn't fix anything.

---

### Post by arnab_das on 2009-11-15
> **neal.m.master said:**
> since i installed from a *.deb, i did this:

sudo dpkg --purge songbird

according to the man page that should have deleted all of the configuration file.

hmm...not exactly.

there's the .config folder. see if there are any remnants of songbird under it. (.config), also check in the .local folder.

---

### Post by nmaster on 2009-11-15
even with songbird installed there is nothing related to songbird in ~/.config:

[email]neal@neal-laptop:~/.config[/email]$ ls
autostart  compiz      gxine        qtcurve.gtk-icons  Trolltech.conf
banshee-1  gnome-session  LyX        real           user-dirs.dirs
bleachbit  gprename      menus        totem           user-dirs.locale
brasero    gtk-2.0      monitors.xml    transmission       vlc

---

### Post by voxman69 on 2009-11-15
I had the exact same problem, only in Spotify. In my case it was Pulseaudio that didn't keep up somehow. I solved it by doing this (credit to the OP, I just can't find that specific thread but i jotted this down):

* Make a new config file called client.conf at this location:
~/.pulse/

* Add a single line to this config file:
autospawn = no

* Then from a command line, kill pulseaudio daemon using:
pulseaudio -k


The autospawn=no thing keeps Pulseaudio from automatically restarting when you kill it. For me this "solved" the problem. Only drawback is that my volume-buttons (or the tray volume) doesn't work with Alsa that's now handling the sound. I use Gnome-Do so I just use that for volume up/down and mute.


To start the Pulseaudio daemon again use: pulseaudio -D

---

### Post by arnab_das on 2009-11-15
btw there's a songbird directory under the tmp folder. delete that and see oif it changes anything.

---

### Post by nmaster on 2009-11-15
> **voxman69 said:**
> I had the exact same problem, only in Spotify. In my case it was Pulseaudio that didn't keep up somehow. I solved it by doing this (credit to the OP, I just can't find that specific thread but i jotted this down):

* Make a new config file called client.conf at this location:
~/.pulse/

* Add a single line to this config file:
autospawn = no

* Then from a command line, kill pulseaudio daemon using:
pulseaudio -k


The autospawn=no thing keeps Pulseaudio from automatically restarting when you kill it. For me this "solved" the problem. Only drawback is that my volume-buttons (or the tray volume) doesn't work with Alsa that's now handling the sound. I use Gnome-Do so I just use that for volume up/down and mute.


To start the Pulseaudio daemon again use: pulseaudio -D


i downgraded to esound in order to get skype to work without cpu leaks.  i don't use pulseaudio.  thanks for the suggestion though

---

### Post by nmaster on 2009-11-15
> **arnab_das said:**
> btw there's a songbird directory under the tmp folder. delete that and see oif it changes anything.

i just tried that.  i'm sure if it changed anything though since i'm not sure how to reproduce the problem.  how could something in /tmp be the problem though?  how could a temporary file create a persistent problem?

---

### Post by nmaster on 2009-11-16
bump

---

### Post by nmaster on 2009-11-19
anyone? i guess no one else has this problem.

---

