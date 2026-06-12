---
title: "Clean up system"
date: 2010-08-07
forum: General Help
---

### Post by TheTiny1 on 2010-08-07
I do not really know where to post this thread so I'll put it here and hope that some one will answer it.
What I want to know is:

What files and programs can be safely removed from ubuntu without any side effects. There are many programs defaulted from the live cd that I will never use and want to remove them. Some are simple but some I am not sure if they can be removed or not.

What I want to do is optimize my system to the least disk space usage as possible.

I also want to know if there is a program out that that I can install that will show me all the details of my system. Something similar to CPUID?

And last but not least is this

What files must be installed to allow a media player to work properly. I like to use VLC player and I seem to be installing a lot of files that I probably do not need to make sure that I get the right ones.

Thanks for any advise.

Bring Blessings
Charles Ellibee
TheTiny1

---

### Post by worksofcraft on 2010-08-07
There isn't really a simple answer because each person has different ideas of what they want to do with their computer. For a start if you don't use spreadsheets and word processing then you might want to remove open office.

Simply use Synaptic Package manager to remove what you think you don't need. If you then find something missing it is easy to reinstall again.

I'm going to experiment with a virtual machine and see if there are any pitfalls.

---

### Post by choochoousmc on 2010-08-07
If you start in upper left corner (ubuntu 10.04), click on applications and system.
A drop down list of the various programs will appear.
You can selectively remove most everything you won't use.
Such as all the games, and the extra internet programs and office programs, etc.
easiest way to remove them is through Ubuntu software center.
Under Applications, scroll to bottom of the list and click it.
When open, on left side click on installed software.
It will display all software installed. Click on remove in each one.
Now under System, you will need to keep the networking, printer, etc.
Most are obvious of what must be kept.

I removed the various video / audio players and installed VLC instead.

these are just suggestions. Final decision is yours.

---

### Post by adok on 2010-08-07
I deleted everything from games, video/audio players (leaving only Rhythmbox), Graphic/Office programs. After everything, maybe using Computer Janitor or Ubuntu-tweak to delete whats left from all this aplications.
In my case this is a server that doesnt do much more then boot and load pidgin.

---

### Post by mike555 on 2010-08-07
If you want a light Ubuntu , Takes Memory use from about 350 to about 100mb.

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

---

### Post by worksofcraft on 2010-08-07
Thanks for that list mike555 :)
I use virtual machines to do software development and testing and so a lot of these less obvious tools have been bloating the virtual environment unnecessarily when I only need to use them on my general purpose main host computer.

p.s. Also thanks to other posts here. Meanwhile the main pitfall I discovered is to avoid removing libraries because some things have built in dependencies even if you don't intend to use that feature.

---

### Post by linux18 on 2010-08-08
for xubuntu and to some extent ubuntu:

```
 printing/scaning:                    
==========        
hplip-data        
smbclient        
foomatic-db        
samba-common-bin    
libsane            
libgs8            
cups-common        
libgutenprint2        
xfprint4        
hpijs


mail:            
=========            
thunderbird        
    

themes/icons:
==========
xfwm-themes
xubuntu-icon-theme            
tango-icon-theme
notify-osd-icons
xcursor-themes
xubuntu-gdm-theme
dmz-cursor-theme
murrine-themes        


fonts:
=========
ttf-unfonts-core
ttf-indic-fonts-core
ttf-takao-pgothic            
ttf-thai-tlwg
ttf-wqy-microhei
xfonts-75dpi


office:            
========        
gnumeric-common        
gcalctool        
abiword-common        
orage            
myspell*        
link-grammer-*
aspell
wamerican
wbritish
dictionaries-common
xfce4-dict


help/documentation:    
==================    
gimp-help-common    
gnumeric-doc        
gnome-doc-utils        
xubuntu-docs
yelp
man-db
manpages


multimedia:
==========
gimp-data
brasero-common
totem-common
woodim
exaile
xubuntu-wallpapers
libgimp2.0
xchat-common
xfce4-mixer


chat/IM:
==========
libpurple0
pidgin-data


editors:
========
vim-runtime
nano


games:
========
gnome-games-common


accessibility:
===============
gnome-orca
gnome-mag
espeak-data
gnome-accessibility-themes
onboard


network:
=========
transmission-gtk
vinagre
w3m


other:
=========
command-not-found-data
bluez
x11-apps
xfce4-xkb-plugin
ubiquity-slideshow-xubuntu
xfce4-screenshooter
jfsutils
xfce4-weather-plugin
xfce4-mailwatch-plugin  
```That pulls 600 MB out of a stock xubuntu install

and this is a shell script for ubuntu:

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
read "remove Bluetooth support (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove bluez-audio bluez-cups bluez-gnome bluez-utils
fi

aa
read "remove evolution mail and Ekiga voip (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove evolution-common evolution-data-server evolution-exchange evolution-plugins evolution-webcal
fi

aa
read "remove various Asian/Arabic fonts (y/n)?"
if [ $x = "y" ]; then
 sudo apt-get remove ttf-arabeyes ttf-arphic-uming ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-thai-tlwg ttf-unfonts-core
fi

aa
read "remove F-spot, Tomboy, Banshee(y/n)?"
if [ $b = "y" ]; then 
 sudo apt-get remove mono-common
fi

aa
read -p "remove openoffice (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove openoffice*
fi

aa
read -p "remove documentation? (y/n)?" x
if [ $x = "y" ]; then
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

aa
read -p "remove printing support (y/n)?" x
if [ $x = "y" ]; then
 sudo apt-get remove cups* hplip* 
fi


####----------------------------------------------------------
####----Log File Utility--------------------------------------

aa
print -p "Summarize log file size (any)?" a
sudo du -hs /var/log/
print -p "empty logs (y/n)?" x
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
 
```this will remove about 700MB from ubuntu


I only wish I had the time to improve the scripts

---

### Post by TheTiny1 on 2010-08-08
I do thank you all for the help. I will be going over what you have given me and see what I can do with it.  

The programs I use are simple Most of Open office I use, vlc, 1 or 2 games, basic internet access, and reading books. 

This is a personal machine I have a business machine that has a whole lot more files and programs than what I will ever need for personal use. 

Again I do thank you for your help in this. 

_Now can someone please advise me as to what files I must install to run VLC player_. I install all gstream files, ubuntu restricted, all Medibuntu files, and any other file that may have something to do with cd/dvd play back.  I know that some of these files are ridiculous but it usually takes me about 2 hours to get VLC player running once I do a new install. 

And one final question is, is there a free version of **CPUID** or something simular?

Thanks a lot and I will put your suggestions to use asap.  

Bright Blessings
Charles Ellibee
TheTiny1

---

### Post by inameiname on 2010-08-08
I'm surprised nobody's mentioned Bleachbit yet. It's in the repos. I use it all the time and it always frees up more than Ubuntu-Tweak, certainly more than Computer Janitor (to which I just remove anyway because it's pretty much useless).

And I'm not sure what CPUID is, but if you are talking about something like System Information in Windows, this is pretty much that, and more:

sudo apt-get install hardinfo


Oh, and if you desire a program to clean up after every install, (just removes the downloaded files automatically after the installation is complete and whatnot):

sudo apt-get install localepurge

---

