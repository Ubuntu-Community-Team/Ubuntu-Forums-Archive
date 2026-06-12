---
title: "my hard drive is &quot;full&quot; (but not)"
date: 2010-08-11
forum: General Help
---

### Post by Scooter_X on 2010-08-11
Hey, I've got 2 partitions - one 20gig for / and another 200gig+ for everything else. I've mounted my everything else's individual folders (docs, videos, music) using fstab. My computer is trying to tell me I'm out of space, and that my biggest culprit is my videos folder. I have tons of movies in there. Thing is, it's telling me that my / partition is the one that's full, and I still have just over 100gb left in my 'everything else' partition. Anyone know what's up? That's crazy.

---

### Post by jakupl on 2010-08-11
open gparted (you probably need to install it) and see which partition is full.

---

### Post by tarps87 on 2010-08-11
Could you post the output of the following
```
df -h
```

---

### Post by dabl on 2010-08-11
or

```
du / | sort -n > du.txt
```

will produce a text file listing directories and their contents (for "/") in descending order of size -- should point you straight to the culprit.

---

### Post by linux18 on 2010-08-11
A simple cleanup shell script, just copy/paste to a text file:
```

#!/bin/bash

####----------------------------------------------------------
####----Functions---------------------------------------------

aa (){
  echo
  echo
  echo
}

####----------------------------------------------------------
####----Intro-------------------------------------------------

aa
echo "Seth's Ubuntu Cleaner"
echo "version 0.01.1    revision 3"

####----------------------------------------------------------
####----Package Cleanup--------------------------------------- 

aa
read -p "remove braile display and screen magnifier (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove gnome-orca brltty brltty-x11 gnome-accessibility-themes gnome-mag libgnome-mag2
fi

aa  
read -p "remove speech synthesizer (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove espeak espeak-data libespeak1 libgnome-speech7
fi

aa
read -p "remove Bluetooth support (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove bluez-audio bluez-cups bluez-gnome bluez-utils
fi

aa
read -p "remove evolution mail and Ekiga voip (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove evolution-common evolution-data-server evolution-exchange evolution-plugins evolution-webcal
fi

aa
read -p "remove various Asian/Arabic fonts (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove ttf-arabeyes ttf-arphic-uming ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-thai-tlwg ttf-unfonts-core
fi

aa
read -p "remove F-spot, Tomboy, Banshee and mono-based programs(y/n)?" b
if [ $b = "y" ]; then 
 sudo apt-get remove mono-common
fi

aa
read -p "remove openoffice (y/n)?" b
if [ $b = "y" ]; then 
 sudo apt-get remove openoffice*
fi

aa
read -p "remove printing support (y/n)?" b
if [ $b = "y" ]; then 
 sudo apt-get remove cups hplip hplip* 
fi

aa
read -p "remove help documentation (y/n)?" b
if [ $b = "y" ]; then 
 sudo apt-get remove ubuntu-docs
fi

####----------------------------------------------------------
####----Cache Cleaner-----------------------------------------

aa
read -p "clean .deb caches (y/n)?" x
if [ $x = "y" ]; then
  sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove 
  sudo rm /var/cache/apt/*.bin 
fi

####----------------------------------------------------------
####----Log File Utility--------------------------------------

aa
read -p "Summarize log file size (any)?" a
sudo du -hs /var/log/
read -p "empty logs (y/n)?" x
if [ $x = "y" ]; then
 cp /dev/null /var/log/*.log
 cp /dev/null /var/log/*/*.log
fi

####----------------------------------------------------------
####----Diagnostics-------------------------------------------

aa
read -p "find rogue files larger than 1GB (y/n)?" x
if [ $x = "y" ]; then 
 sudo find / -name '*' -size +1G
fi 

aa
read -p "find rogue files larger than 500MB (y/n)?" x
if [ $x = "y" ]; then 
 sudo find / -name '*' -size +500M
fi

aa
read -p "print total disk usage on all partitions (y/n)?" x
if [ $x = "y" ]; then
 df -Th | grep -v "fs" | sort
fi

####----------------------------------------------------------
####----Outro-------------------------------------------------

aa
echo "DONE"

####----------------------------------------------------------
####----------------------------------------------------------

 
```then chmod +x the_script

then ./the_script

---

### Post by Scooter_X on 2010-08-12
Yea, thanks guys. I wound up installing gparted to see. I was literally at 100% on that partition tho, and I had to delete some games I had recently installed and was trying out. Thing that threw me off was the disk analyzer, it was showing me some stuff I didn't get. (the whole 'videos' thing on the other partition for example) Anyway, manually deleted the files, that didn't seem to help. I even emptied the 'dustbin' and it still showed that I was at 100% after I refreshed the disk analyzer. Anyway, restarted and then I had my space back, installed gparted, checked, I was OK. I've only got 20gb tho on my / partition, and I'd been installing all kinds of games lately just to check them out. I've been bored I guess. 

(I settled on ut2k4's Alien Swarm mod, just in case anyone was wondering. Totally dig it)

---

### Post by dino99 on 2010-08-12
you can install bleachbit to make room on your disk

---

