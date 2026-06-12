---
title: "Pandora Radio"
date: 2010-08-17
forum: General Help
---

### Post by fusky on 2010-08-17
HI ,still new to ubuntu and still trying to get this but if anyone could help thanks.but im having a problem loading pandora internet radio.I have tried going to there main site and it would only load about 50% of the way so i tried installing adobe flash plugin for firefox but i still get the same problem still ,so then i tried going to there main site and downloading manually from there but ive seem to hit a snag , i have no idea on how to install a YUM for linux,or .tar.gz , or .rpm or .deb for ubuntu 8.04 or Apt for Ubuntu 9.04. ive downloaded some and extracted but i dont know how you can run them or anything right now im using ubuntu 10.04 if thats of any help .Thanks

---

### Post by earthpigg on 2010-08-17
hi,

can you show us the .deb that you are considering downloading and installing?

to install a .deb, download it to your desktop and double click on it. this usually isn't necessary, though. if you show us what you are thinking of downloading/installing, we can probably provide some feedback.

---

### Post by bug67 on 2010-08-17
Are you trying to install the Pandora desktop app?  If so, you need to download the [Adobe AIR .deb]("http://get.adobe.com/air/otherversions/"), double click to install and then, download the Pandora desktop app.  The Pandora desktop app is reliant on Adobe AIR for it's install.

If you're just trying to play Pandora from their web site and having problems, I dunno.  Could be you need a faster internet connection?  Try setting quality settings to "normal" instead of "high."  This *could* help reduce the ammount of bandwidth needed for streaming.  Pandora is extremely resorce hungry.  Might see if any other processes are using bandwidth and disable the less than needed ones.  I'm grasping at straws...

---

### Post by MockY on 2010-08-17
The easiest would probably be to install a Linux native Pandora client. 
Use Pithos

IN order to install it, launch the good ol terminal and type the following:
```
sudo add-apt-repository ppa:kevin-mehall/pithos-daily 
```
Which will add the repository where Pithos is located
Then simply paste this into the terminal:
```
sudo apt-get update && sudo apt-get install pithos 
```

It should then be located under the Sound & Video menu

---

### Post by fusky on 2010-08-17
> **earthpigg said:**
> hi,

can you show us the .deb that you are considering downloading and installing?

to install a .deb, download it to your desktop and double click on it. this usually isn't necessary, though. if you show us what you are thinking of downloading/installing, we can probably provide some feedback.

All the listed files were for the adobe flash player plugin not sure if pandora uses flash but since almost evrything uses it  i thought it was the best bet

---

### Post by fusky on 2010-08-17
> **bug67 said:**
> Are you trying to install the Pandora desktop app?  If so, you need to download the [Adobe AIR .deb]("http://get.adobe.com/air/otherversions/"), double click to install and then, download the Pandora desktop app.  The Pandora desktop app is reliant on Adobe AIR for it's install.

If you're just trying to play Pandora from their web site and having problems, I dunno.  Could be you need a faster internet connection?  Try setting quality settings to "normal" instead of "high."  This *could* help reduce the ammount of bandwidth needed for streaming.  Pandora is extremely resorce hungry.  Might see if any other processes are using bandwidth and disable the less than needed ones.  I'm grasping at straws...

Sorry, i am trying to stream from there website i know i can since i was able to in windows without any interuptions and the player only loads halfway so i thought it might be a plugin issue not really sure.

---

### Post by fusky on 2010-08-17
> **MockY said:**
> The easiest would probably be to install a Linux native Pandora client. 
Use Pithos

IN order to install it, launch the good ol terminal and type the following:
```
sudo add-apt-repository ppa:kevin-mehall/pithos-daily 
```Which will add the repository where Pithos is located
Then simply paste this into the terminal:
```
sudo apt-get update && sudo apt-get install pithos 
```It should then be located under the Sound & Video menu

Thanks this one did help me wasn't looking in going into the terminal just to install anything but i guess it will have to do ,the player works but was hoping to just be able to run it in the web based player,but it works and im happy to get my free music back :D

---

### Post by earthpigg on 2010-08-17
> **fusky said:**
> > hi,

can you show us the .deb that you are considering downloading and installing?

to install a .deb, download it to your desktop and double click on it. this usually isn't necessary, though. if you show us what you are thinking of downloading/installing, we can probably provide some feedback.

All the listed files were for the adobe flash player plugin not sure if pandora uses flash but since almost evrything uses it  i thought it was the best bet

oh. we don't install flash by downloading/installing a .deb from a website, we do so by searching the software center for "*ubuntu restricted extras*", and installing it.

restart firefox.

if that doesn't do it for you, look for 'flash installer' in the software center and install it.

:)

downloading software from random websites is, in general, the absolute ***last*** resort of an Ubuntu user.

---

