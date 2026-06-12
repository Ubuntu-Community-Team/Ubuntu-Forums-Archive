---
title: "Making an install script, am i missing anything important?"
date: 2010-03-29
forum: General Help
---

### Post by HPD2 on 2010-03-29
Lately I have been working on a script, one with apt-get and with aptitude, to install the GUI desktop from a basic CLI install of Ubuntu. My question is, am I leaving any thing important out, or is there any thing important I should add?
```
#!/bin/bash
echo "[*] Updating Repos"
sudo apt-get update
sudo apt-get upgrade
#
echo "[*] Installing Gnome Essentials"
sudo apt-get -y install gnome-core
sudo apt-get -y install gdm
sudo apt-get -y install wicd
sudo apt-get -y install indicator-applet-session
sudo apt-get -y install human-theme
sudo apt-get -y install x11-xserver-utils
sudo apt-get -y install tangerine-icon-theme
sudo apt-get -y install gnome-themes-ubuntu
sudo apt-get -y install ubuntu-artwork
sudo apt-get -y install jockey-gtk
sudo apt-get -y install gnome-screensaver
sudo apt-get -y install gnome-utils
sudo apt-get -y install alsa-utils
sudo apt-get -y install blueman
sudo apt-get -y install ubuntu-laptop-mode
sudo apt-get -y install system-config-printer-gnome
sudo apt-get -y install update-manager
sudo apt-get -y install powernowd
sudo apt-get -y install ntfsprogs
sudo apt-get -y install synaptic
sudo apt-get -y install gdebi
sudo apt-get -y install apmd
#
echo "[*] Installing Application Essentials"
sudo apt-get -y install firefox 
sudo apt-get -y install thunderbird 
sudo apt-get -y install transmission 
sudo apt-get -y install pidgin
sudo apt-get -y install openoffice.org
sudo apt-get -y install rhythmbox
sudo apt-get -y install f-spot
sudo apt-get -y install totem
sudo apt-get -y install gimp
sudo apt-get -y install gnome-do
sudo apt-get -y install compiz
sudo apt-get -y install gufw
sudo apt-get -y install brasero
sudo apt-get -y install ubuntu-restricted-extras
sudo apt-get -y install gnome-nettool
sudo apt-get -y install ubuntustudio-look
sudo apt-get -y install compizconfig-settings-manager
sudo apt-get -y install file-roller
sudo apt-get -y install nautilus-wallpaper
sudo apt-get -y install nautilus-open-terminal
sudo apt-get -y install ttf-mscorefonts-installer
#
echo "[*] Enable Firewall"
sudo ufw enable
#
echo "[*] Clean up"
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
#
echo "[*] !Reminder!"
echo "Edit /etc/network/interfaces comment out 'Primary network interface'"

```
I do know I don't need to put each package on a new line but its easier to read like this IMO.

---

### Post by HPD2 on 2010-03-30
suggestions, advice, anything?

---

### Post by drumkitcat on 2010-04-02
I ended up going with Evolution originally because I wanted to use thunderbird but could not figure out how to get it installed.... until last night!

Honest to god, the best and easiest way to get the latest stable version of thunderbird installed is to add the Ubuntuzilla repository - and then install thunderbird - it's the fastest and easiest thing I've ever done.

Now I'm running Thunderbird, and I gotta say it's worth it - I like it much more than Evolution, and it's totally more intuitive as I use Gmail as my email - Thunderbird set it up automatically, unlike Evolution where I had to dink around with the port settings, etc.

To recap:  install the ubuntuzilla repository (just do a google search for the sourceforge ubuntuzilla site) and then install Thunderbird - nothing could be easier.

Forget the script creation, or downloading tarball versions - that's fine and it works if you know what your doing, but otherwise, why not take the automated approach?

Best of luck to you
Paul

---

### Post by Chesamo on 2010-04-02
Something like this?

[http://ubuntuforums.org/showthread.php?t=1670396](http://ubuntuforums.org/showthread.php?t=1670396)
[http://minimal-desktop.blogspot.com/](http://minimal-desktop.blogspot.com/)

(also: apt-get can take more than one installation command, see my script)

---

### Post by john newbuntu on 2010-04-02
From a working Ubuntu machine, if you run:
```
dpkg --get-selections > installed-software
```

and save the file in some place safe(of course you can add/remove stuff from here), you can then restore all your software using:

```

dpkg --set-selections < installed-software
sudo apt-get install dselect
sudo apt-get -y update
sudo apt-get dselect-upgrade
```


Also look at trakerjohn's exhaustive list of stuff for Karmic:
[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)

---

### Post by HPD2 on 2010-04-03
@ Drumkitcat I am making the scripts so I don't have to sit down and type every thing out after i install the CLI (Command Line Interface). All i have to do is install the CLI then a few commands to mount the USB drive then execute the script. Once I do that it gets me the "Ubuntu desktop" with out a lot of the extra stuff I never use and don't need.

Its easier to build up than to strip down.

@ Chesamo I got the idea from this post [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961) 
Not really looking for any thing as robust as whats in your links, yet. I also know I could have just used apt-get and listed the packages after that, but I think trying to read the script when done like that can be difficult. Although with my second script (install.sh) I did that but using aptitude.

@ john newbuntu Wouldn't that be more useful if I was backing up the system?

Really I am more or less looking for some thing important that I have left out, couldn't think of anything my self so i decided to ask the community.

---

### Post by ron999 on 2010-04-03
Hi
Will you be needing a media plugin for firefox?
Such as gecko-mediaplayer or mozilla-plugin-vlc or similar.

---

### Post by HPD2 on 2010-04-03
> **ron999 said:**
> Hi
Will you be needing a media plugin for firefox?
Such as gecko-mediaplayer or mozilla-plugin-vlc or similar.

Not sure, haven't ran in to any issues playing anything in FireFox yet.

---

### Post by john newbuntu on 2010-04-04
HPD2.  The method that I mentioned can be used for backing up as well.  It depends on the *buntu flavor that you are running on.  If run on Karmic, it installs Karmic software.  If run on Lucid, it installs the Lucid versions and so on.

---

