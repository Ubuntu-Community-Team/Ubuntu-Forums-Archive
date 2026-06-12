---
title: "Before I install Ubuntu..."
date: 2011-04-17
forum: General Help
---

### Post by mg1234 on 2011-04-17
When my computer (a Vaio LT1M) comes back from the repair shop, I'm going to install Ubuntu again - I had to reinstall Vista for them to take it. Last time I installed linux, a couple of the pieces of hardware didn't work out of the box. I was wondering if you can tell me how to install them, so I won't come into trouble when I get it back :)
 
1. AverMedia M115S TV Tuner Card (and some kind of Windows Media Center substitute)
 
[COLOR=black]2. Sony "MotionEye" Camera - [/COLOR][COLOR=black]Ricoh Camera Driver 6..209G 6.1005.209.0 (and some kind of replacement to PhotoBooth)[/COLOR]
 
3. SD Card Reader/Writer
 
[COLOR=black]Also, do you have any seperate application recomendations? In particular Linux replacements for iTunes (with decent support for my iPod Classic), IDM, uTorrent, Microsoft Office, Windows Live Messenger. Spotify, Photoshop and MP3Tag. In fact, anything.[/COLOR]
 
Thanks ):P

---

### Post by Spyderkid on 2011-04-17
get VLC as the replacement windows media centre.

a application called cheese booth comes with ubuntu standard you can use that as the photo booth

>Spotify works fine on wine
[SEE HERE HOW TO MAKE IT WORK]("http://ubuntuforums.org/showthread.php?t=1693743")

[SEE HERE ON HOW TO USE WINE]("http://ubuntuforums.org/showthread.php?t=1692341")



>for photoshop use GIMP image editor

>windows live messenger use Empathy or Pidgin

>for uTorrent you can use bitTorrent

>microsoft word use Libre Office find it on the internet.

>use GTK-POD for your ipod

---

### Post by daniel_w93 on 2011-04-17
Okay so...

1. check out this site for your TV Card installation
[http://www.linuxtv.org/wiki/index.php/User_Information]("http://www.linuxtv.org/wiki/index.php/User_Information")
the you can access it and watch tv with apps like MythTv or TVtime

2. With any newer Ubuntu (10.04 or 10.10) the cam should work out of the box for using it, get Cheese Webcam Booth from the Software Center

3. I don't understand the question...If theres an SD Card slot on your computer it should work...if there's none just buy any USB SD Card Reader

for the all the other stuff:

Rhythmbox is installed by default you can access your iPod from it...but can't sync it for all I know....perhaps Banshee Media Player has better support they both have access to the UbuntuOne Music Store where you can buy music just like on iTunes...but without drm :P
if iPod syncing doesn't work you need to get gtkPod from the Software Center to put music, video etc. on it 

For IDM you'd have to dig around yourself...I don't know about that stuff...just search the Software Center

BitTorrent is installed by default...though I use FatRat to download stuff...cause you can search through all major torrent sites with it.

OpenOffice is installed by default though any hard line opensource guy would tell you to kick it out and use LibreOffice instead (cause OpenOffice went closed code or something)

The default Messenger Client installed is Empathy you can add any Chat profile you want to it (AIM, MSN, Yahoo, Facebook Chat etc.)

As a spotify substitute you might wanna look into Miro Internet TV, the Banshee Media Player or Boxee 
[http://www.boxee.tv/]("http://www.boxee.tv/")

For Photoshop there's Gimp

And MP3Tag is really unneccesary cause you can edit the tags and Album Art inside Rhythmbox or Banshee


Also for dvd support you want to get the libdvdcss2 and GNOME Media Player with all video engines available
...again all in the Software Center


EDIT: For Spotify....what he said xD

---

### Post by kseise on 2011-04-17
> **daniel_w93 said:**
> :

Rhythmbox is installed by default you can access your iPod from it...but can't sync it for all I know....perhaps Banshee Media Player has better support they both have access to the UbuntuOne Music Store where you can buy music just like on iTunes...but without drm :P
if iPod syncing doesn't work you need to get gtkPod from the Software Center to put music, video etc. on it

Rhythmbox and Banshee should both be able to sync an iPod classic.  Both of those programs along with the GTKPod program use the same libraries to enable communication (libgpod).  The iPod classic is well supported.  Try all three and see which one you like the best.

---

### Post by Old_Man_Unix on 2011-04-17
re Open Office vs Libreoffice:

OOo is still FOSS but even so there are good reasons to go with Libreoffice.  If you install any current release of Ubuntu (until Natty is official), you will get OOo by default.  You can install Libreoffice by adding the PPA.  

The PPA for Libreoffice is: **'ppa:libreoffice/ppa'.  **Add that PPA to your software sources and you will be good to go.

I strongly suggest you install the application by adding the  PPA  rather than downloading the .deb package(s) from the website.  You will then get all the Libreoffice updates  automatically as part of your regular updating process.

Also, don't forget to install the **GNOME-integration** package for  Libreoffice as  well.  It isn't installed automatically.   Also, if you need additional  language packs or fonts, you should install those too.

---

