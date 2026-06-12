---
title: "Stuff to do when reinstalling Ubuntu (your linux cheatsheet)"
date: 2010-07-05
forum: General Help
---

### Post by danbuter on 2010-07-05
Not sure if anyone else does this but I have a checklist of programs and commands that I keep. Some of it I use immediately after installing the latest Ubuntu, others I just use periodically. I was curious if anyone else did this, and what they used.


My list:

programs to install:
Avant Window Manager (AWN)
secure delete
chkrootkit 
gedit-plugins
gstreamer-plugins ugly
flashplugin non-free
msttcorefonts


After AWN set up

sudo chmod -x /usr/bin/gnome-panel    #turns off Gnome panel - requires restart
sudo chmod +x /usr/bin/gnome-panel    #turns on Gnome panel - requires restart


cd ~/.local/share/Trash   # path to Trash bin


Secure Delete commands
srm   # securely deletes file
smem  # securely wipes RAM


Set Ctrl-Alt-Backspace to kill X
Go to System->Preferences->Keyboard
Go to Layouts Tab
Click Options
Expand "Key sequence to kill the X-server"
Check "C-A-B"

---

### Post by lkjoel on 2010-07-05
> **danbuter said:**
> Not sure if anyone else does this but I have a checklist of programs and commands that I keep. Some of it I use immediately after installing the latest Ubuntu, others I just use periodically. I was curious if anyone else did this, and what they used.


My list:

programs to install:
Avant Window Manager (AWN)
secure delete
chkrootkit 
gedit-plugins
gstreamer-plugins ugly
flashplugin non-free
msttcorefonts


After AWN set up

sudo chmod -x /usr/bin/gnome-panel    #turns off Gnome panel - requires restart
sudo chmod +x /usr/bin/gnome-panel    #turns on Gnome panel - requires restart


cd ~/.local/share/Trash   # path to Trash bin


Secure Delete commands
srm   # securely deletes file
smem  # securely wipes RAM


Set Ctrl-Alt-Backspace to kill X
Go to System->Preferences->Keyboard
Go to Layouts Tab
Click Options
Expand "Key sequence to kill the X-server"
Check "C-A-B"
Why would you want to remove gnome-panel?
And why would you want to kill X?

---

### Post by danbuter on 2010-07-05
I don't need gnome panel when I have Awn.
There's a hundred reasons to kill X if a bug happens.

---

### Post by danbuter on 2010-07-05
Am I the only person who does this? I was hoping more people would share, so that newer users could learn some nice tricks.

---

### Post by lkjoel on 2010-07-05
> **danbuter said:**
> Not sure if anyone else does this but I have a checklist of programs and commands that I keep. Some of it I use immediately after installing the latest Ubuntu, others I just use periodically. I was curious if anyone else did this, and what they used.


My list:

programs to install:
Avant Window Manager (AWN)
secure delete
chkrootkit 
gedit-plugins
gstreamer-plugins ugly
flashplugin non-free
msttcorefonts


After AWN set up

sudo chmod -x /usr/bin/gnome-panel    #turns off Gnome panel - requires restart
sudo chmod +x /usr/bin/gnome-panel    #turns on Gnome panel - requires restart


cd ~/.local/share/Trash   # path to Trash bin


Secure Delete commands
srm   # securely deletes file
smem  # securely wipes RAM


Set Ctrl-Alt-Backspace to kill X
Go to System->Preferences->Keyboard
Go to Layouts Tab
Click Options
Expand "Key sequence to kill the X-server"
Check "C-A-B"

sudo chmod -x /usr/bin/gnome-panel    #turns off Gnome panel - requires restart
sudo chmod +x /usr/bin/gnome-panel    #turns on Gnome panel - requires restart

interesting...
I would rename the file.

---

### Post by btindie on 2010-07-05
Off the top of my head, some of the first things I do are.
 
Fix sudo so I don't need to type in my password everytime.
 
Setup ~/.bash_aliases to include(I got this from using openSUSE)
```
alias l='ls -alF'
```
 
Edit ~/.bashrc to source ~/.bash_aliases
 
Customise ~/.nanorc to use the settings I like
 
Copy my SSH private/public key to ~/.ssh/
 
'chmod -x' the os prober grub script so it doesn't list every available OS on my box.
 
this is part of my 'base build'. Then the software I install depends on what I'm using it for.

---

### Post by Troublegum on 2010-07-05
> **danbuter said:**
> Am I the only person who does this? I was hoping more people would share, so that newer users could learn some nice tricks.

No, you're not. I've written a bash script that adds a few ppa's, installs all my programs, restores their config, setup my infrared-receiver and lirc, restores my samba config, etc ...

The list of installed programms include:
[LIST]
[*]Sun Java
[*]VirtualBox
[*]Samba
[*]Guake
[*]Docky
[*]Lirc/irserver
[*]tvtime
[*]flash
[*]vlc
[*]texlive
[*]nxtvepg
[*]wine
[/LIST]

I backed up the config files for theses programs (some use gconf like docky, some use simple config-files in $HOME), so the script turns a fresh ubuntu installation into the system I'm used to in a matter of minutes.

---

### Post by WorMzy on 2010-07-05
> **btindie said:**
> Fix sudo so I don't need to type in my password everytime.

A sudo that doesn't require password verification sounds inherently broken to me, not "fixed". ;)

I:
[LIST]
[*]Install compiz/compiz-fusion, all plugins, ccsm and emerald
[*]Import my compiz-config
[*]Import my Shining Brightly custom Emerald theme
[*]Install gnome-color-chooser
[*]Import my gnomecc theme for the current season
[*]Install electricsheep and set it as my screensaver
[*]Install lm_sensors, hddtemp, conky-all, and conky-forecast
[*]Import my .conkyrc, .conkyforecast, and .scripts/
[*]Install LAMP via tasksel
[*]Import my websites
[*]Install weechat
[*]Import my weechat settings
[*]Install mpd and sonata
[*]Install vlc
[*]Install gimp
[*]Install parcellite
[*]Install shutter
[/LIST]

I don't follow a cheatsheet or anything, but I always end up with these programs; although mpd/sonata and parcellite are new -- I've used Amarok2, Exaile, and Rhythmbox throughout my years playing with Linux, mpd is my latest kick. And I used to use glipper instead of parcellite.

---

### Post by Telengard C64 on 2010-07-05
I don't really have a cheat sheet like this, but for every fresh install of my system I usually install the same stuff. BTW, I am a Kubuntu user so some of this doesn't apply to Ubuntu.

**_What I Do On A Fresh Install_**

[list]
[*]Don't trust KPackageKit to install **anything**! Instead use [_apt-get_](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto) or [_aptitude_](https://help.ubuntu.com/community/AptitudeSurvivalGuide) inside a [_Konsole_](https://help.ubuntu.com/community/CommandlineHowto?action=show&redirect=Console#How%20to%20invoke%20it) window

[*][_bash-doc_](http://packages.ubuntu.com/search?keywords=bash-doc&searchon=names&exact=1&suite=all&section=all) is *The GNU Bash Reference Manual* in [_info form_](https://help.ubuntu.com/community/UsingTheTerminal#%22Man%22%20and%20getting%20help)

[*][_build-essential_](https://help.ubuntu.com/community/CompilingSoftware)

[*][_gcc-doc_](http://packages.ubuntu.com/search?keywords=gcc-doc&searchon=names&suite=all&section=all)

[*][_glibc-doc_](http://packages.ubuntu.com/search?keywords=glibc-doc&searchon=names&suite=all&section=all)

[*][_p7zip-full_](https://help.ubuntu.com/community/FileCompression#7zip%20(.7z)) and [_unrar_](https://help.ubuntu.com/community/FileCompression#Rar%20(.rar))

[*][_Firefox Web Browser - Community Ubuntu Documentation:_](https://help.ubuntu.com/community/Firefox)
[list]
[*][_NoScript - JavaScript/Java/Flash blocker for a safer Firefox experience! - what is it? - InformAction:_](http://noscript.net/)
[/list]

[*][_kubuntu-restricted-extras_](https://help.ubuntu.com/community/RestrictedFormats)
[list]
[*]*Installing this package will pull in support for MP3 playback and decoding, Java runtime environment, Flash plugin, DVD playback, and LAME (to create compressed audio files).*

[/list]

[*][_SMPlayer - Community Ubuntu Documentation:_](https://help.ubuntu.com/community/SMPlayer)
[list]
[*]brings [_mplayer-nogui_](http://packages.ubuntu.com/search?keywords=mplayer-nogui&searchon=names&suite=all&section=all) with it

[*]be sure to get [_mozilla-mplayer_](http://packages.ubuntu.com/search?keywords=mozilla-mplayer&searchon=names&exact=1&suite=all&section=all) for playback inside Firefox

[/list]

[*][_Setting Up Samba - Community Ubuntu Documentation:_](https://help.ubuntu.com/community/SettingUpSamba)

[*][_The GIMP - The GNU Image Manipulation Program - Community Ubuntu Documentation:_](https://help.ubuntu.com/community/TheGIMP)

[*][_KeePassX:_](http://www.keepassx.org/)

[*][_KAlarm_](http://packages.ubuntu.com/search?keywords=kalarm&searchon=names&exact=1&suite=all&section=all)

[*][_EmacsHowto - Community Ubuntu Documentation:_](https://help.ubuntu.com/community/EmacsHowto)

[*][_ClamAV - Community Ubuntu Documentation:_](https://help.ubuntu.com/community/ClamAV)

[/list]

**_More Ideas_**

[list]
[*][_quick guide for windows to kubuntu karmic transitioners:_](http://kubuntuforums.net/forums/index.php?topic=3108924.0)
[*][_Karmic - Kubuntuguide:_](http://kubuntuguide.org/Karmic)
[/list]

---

### Post by lkjoel on 2010-07-06
Here are my apps that I would install:
(The sub bullets are less essential)


[LIST]
[*]WINE
[*]LinuxEssentials (check on my sig)
[*]OSS, depending if the sound works or not (check Fix my sound in my sig)
[*]GIMP
[*]OpenOffice.org the whole suite
[*]PlayOnLinux
[*]Flash
[LIST]
[*]BlackBox
[/LIST]

[LIST]
[*]IceWM
[/LIST]
[*]Once the project is finished, Terminal Enhancements (check on my sig)
[/LIST]

---

### Post by bodhi.zazen on 2010-07-06
> **danbuter said:**
> Am I the only person who does this? I was hoping more people would share, so that newer users could learn some nice tricks.

After an installation, customization becomes personal, so there is no single list of what to do.

If you are interested, search these forums and you will find many similar threads.

---

### Post by tweaked on 2010-07-06
> **danbuter said:**
> Am I the only person who does this? I was hoping more people would share, so that newer users could learn some nice tricks.

This one caught my eye. So many don't seem to understand, newer users have no clue what you just did and really don't want anything to do with a command line.

---

### Post by Telengard C64 on 2010-07-06
> **tweaked said:**
> newer users have no clue what you just did and really don't want anything to do with a command line.

It is always sad to witness another human being lose the battle against willful ignorance. What can one do?

---

### Post by pricetech on 2010-07-06
Why assume willful ignorance ??  I would think it's more like just wanting to get the system usable so they can learn what they need to know with that usable system.

I have a cheat sheet I use, but it seems to evolve at each install.  Still it helps me remember everything I need to do to get the system the way I want it.

As Bodhi Zazen says, it's a personal thing, so I'm not posting my cheat sheet since it's the way "I" want it set up and may have no similarity to what anyone else wants.

---

### Post by kingbirdy on 2010-07-06
> **tweaked said:**
> This one caught my eye. So many don't seem to understand, newer users have no clue what you just did and really don't want anything to do with a command line.
I want everything to do with the command line, and I've been doing this for five days now. I spend all my time on the machine on the internet, in the terminal, or screwing with my Conky.

---

### Post by The Cog on 2010-07-06
A few of my customisations:

Remove that envelope from the notification area:
sudo apt-get remove indicator-messages


Remove mono:
apt-get purge libmono* libgdiplus cli-common libsqlite0 libglitz-glx1 libglitz1

Disable CapsLock - (add this to ~/.bashrc):
xmodmap -e "remove lock = Caps_Lock"
#xmodmap -e "add lock = Caps_Lock"

And my netbook shuts down as soon as power is unplugged unless I do this:
Press Ctrl-Alt-F2 and use the pop-up to launch gconf-editor. 
Navigate to Apps / gnome-power-manager / general. 
De-select the option use_time_for_policy.

---

### Post by Telengard C64 on 2010-07-06
> **kingbirdy said:**
> I want everything to do with the command line, and I've been doing this for five days now. I spend all my time on the machine on the internet, in the terminal, or screwing with my Conky.

Good for you! That's a great attitude IMHO :D

Here's the customization I recommend for your command line learning:

```
$ aptitude show bash-doc
. . .
Description: Documentation and examples for the The GNU Bourne Again SHell
 Bash is an sh-compatible command language interpreter that executes commands
 read from the standard input or from a file.  Bash also incorporates useful
 features from the Korn and C
 shells (ksh and csh).

 This package contains the documentation in info format, all the examples and
 the main changelog.
$ sudo aptitude install bash-doc
$ info bashref
```

This one is optional, but still very educational and well worth your time:

```
$ sudo aptitude install rutebook
```

After the rutebook package is installed use your file manager or browser (Nautilus, Konqueror, Dolphin or whatever) to browse to the folder **/usr/share/doc/rutebook**. The book is in a gzipped PDF, or you can just open **/usr/share/doc/rutebook/html/index.html** to read in your web browser.

Have fun  ;)

---

### Post by warfacegod on 2010-07-06
The one thing I *forget* to do on every single new install I do is get the p7zip-full package that's required by unetbootin. It never fails.

---

