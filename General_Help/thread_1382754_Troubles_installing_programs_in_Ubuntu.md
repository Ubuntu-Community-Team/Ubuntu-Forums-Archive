---
title: "Troubles installing programs in Ubuntu"
date: 2010-01-16
forum: General Help
---

### Post by PDA1 on 2010-01-16
I'm new to Linux and have a lot of problems installing and deleting programs.

Show you what I mean;

I've been trying to install Thunderbird 3.0 (NOT Shredder).

I've been told to install it via Synaptic, Ubuntuzilla, deb, Tar ball, PPA and countless other "really easy" methods that have all led to no installation, countless hours of wasted time, and no running of TB3.

I do the download and extract routine with no results.

Oh sure....through brute force and stupidity I end up with TB3 in the /opt/Thunderbird folder.  But will it run?  Of course not.  Can I run it in Terminal?  Sure, once the DJIA (Dow Jones Industrial Average) goes back to 14,000!

I have NO IDEA how to install programs like TB3 and sure as heck it won't install and run using Synaptic.....not on my machine.

I've read the posts about installing it....but it never works for me.


There has to be something seriously messed up on my machine that stops, blocks or prevents installation of TB3.  Maybe there's something messed up in Software Sources (or whatever it's called)?


Is there anyone that can step me through an absolutely fool (me) proof installation of TB3?

Please, don't just say, "download from Mozilla....click here".  Those installations have never been successful. 

This is SO frustrating!

Thank you.

---

### Post by Penguin Guy on 2010-01-16
I would advise just installing Thunderbird 2, it'll be a lot easier and a lot more stable. I have included instruction on installing both, it's your choice.

To install Thunderbird 2:
[LIST=1]
[*]Remove all previous attempted installations
[*]Click [here]("apt:thunderbird")
[*]Click "Install"
[/LIST]

To install Thunderbird 3:
[LIST=1]
[*]Remove all previous attempted installations
[*]Open the terminal (Press [COLOR="Green"]Alt + F2[/COLOR], then type [COLOR="green"]gnome-terminal[/COLOR])
[*]Copy and paste the following into the terminal
```

echo -e "\n# Mozilla Repository (http://ubuntuforums.org/showpost.php?p=8674623)\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29 && sudo apt-get update && sudo apt-get install thunderbird-mozilla-build && echo "===== THUNDERBIRD INSTALLED SUCCESSFULLY ====="

```
[*]Press return and enter your password whenever asked
[/LIST]

To **un**install Thunderbird 3:
[LIST=1]
[*]Open the terminal (Press [COLOR="Green"]Alt + F2[/COLOR], then type [COLOR="green"]gnome-terminal[/COLOR])
[*]Copy and paste the following into the terminal
```

sudo apt-get purge thunderbird-mozilla-build && sudo apt-key adv --delete-keys C1289A29 && grep -Exv "# Mozilla Repository (http://ubuntuforums.org/showpost.php?p=8674623)|deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" /etc/apt/sources.list | sudo tee /etc/apt/sources.list > /dev/null && sudo apt-get update && echo "===== THUNDERBIRD UNINSTALLED SUCCESSFULLY ====="

```
[*]Press return and enter your password whenever asked, if it pauses and asks if you want to continue, press "y" then enter
[/LIST]


Hope that helps.

---

