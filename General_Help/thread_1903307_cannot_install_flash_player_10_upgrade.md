---
title: "cannot install flash player 10 upgrade"
date: 2012-01-02
forum: General Help
---

### Post by janetk on 2012-01-02
I have Ubuntu 10.04 in 32 bit machine with Firefox 3.6.24 for Ubuntu. I cannot see some videos and get a message to upgrade Flash player. The options given are .rpm and .targz. I can download either of these and can unpack them. I do not get a .deb file offered. Firefox does not find the upgrade and I cannot seem to do an install. 
Is there a .deb download anywhere?
Do I have to use alien?
Do I have to use the command line? what do I write?
why is there no upgrade in the Ubuntu applications packages?
Do I have to have Chrome rather than Firefox?
Please help! Thanks

---

### Post by crazy bird on 2012-01-02
Install this add-on for Firefox: [Flash-aid]("http://www.webgapps.org/add-ons/flash-aid"). This add-on will help you install the correct flash player and removing all conflicting flash players.

---

### Post by flipper T on 2012-01-02
there is a firefox add on called ¨flash aid¨

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss)

install and run this from the browser

it normally resolves flash issues.

---

### Post by Unitux on 2012-01-02
download tar.gz, copy libflashplugin.so to "~/.mozilla/plugins/".

---

### Post by sammiev on 2012-01-02
> **Unitux said:**
> download tar.gz, copy libflashplugin.so to "~/.mozilla/plugins/".

Flash-aid will let you know when you need to update. I prefer the other method myself but you need root access to move libflashplugin.so to "~/.mozilla/plugins/".

---

### Post by janetk on 2012-01-02
thank you but I still have not cracked the problem.
As you have suggested, I have installed the flash aid add-on, restarted firefox, and set flash aid to find updates.
I then went to a couple of the sites where videos gave me the update Flash player message and they still do show the message rather than the video.
The download (install-flash-player-10-linex.tar.gz) was previously downloaded into the download area of home. I unzipped it there. So I have the folder install_flash_player_10_linux and that folder holds usr and libflashplayer.so
I take it that this last file has to be moved to ~/.mozilla/plugins/
I have only rarely used the command line. I have root access but do not use it unless I know exactly what to type. 
A little more help would be greatly appreciated.

---

### Post by flipper T on 2012-01-02
out of interest, what sites are you visiting ?

don´t be shy, not easily shocked :)

---

### Post by trickstar on 2012-01-02
try this 

Remove currently installed versions of Flash.

       sudo apt-get purge flashplugin-nonfree flashplugin-installer gnash gnash-common mozilla- v       plugin-gnash swfdec-mozilla
       sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
       sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
       sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
       sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
       rm -f ~/.mozilla/plugins/*flash*so


sudo apt-add-repository ppa:sevenmachines/flash
       sudo apt-get update
       sudo apt-get install flashplugin-installer

---

### Post by gandaran on 2012-01-02
> I take it that this last file has to be moved to ~/.mozilla/plugins/
I have only rarely used the command line. I have root access but do not use it unless I know exactly what to type. 
A little more help would be greatly appreciated.
no root access is needed for user settings, just enable show hidden files on home folder then move the flash .so file to .mozilla/plugins folder, you will have to create the plugins folder as it doesn't exist there.
I don't recommend using this method of manually installing flash as you are going to forget about it, it doesn't update and may conflict with other system installed flash plugins, your best bet is the firefox flash-aid addon to remove every conflicting plugin and just install one system flash plugin for every browser.

---

### Post by gandaran on 2012-01-02
> **trickstar said:**
> try this 

Remove currently installed versions of Flash.

       sudo apt-get purge flashplugin-nonfree flashplugin-installer gnash gnash-common mozilla- v       plugin-gnash swfdec-mozilla
       sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
       sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
       sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
       sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
       rm -f ~/.mozilla/plugins/*flash*so


sudo apt-add-repository ppa:sevenmachines/flash
       sudo apt-get update
       sudo apt-get install flashplugin-installer
the sevenmachines ppa was for 64-bits flash and no longer exists

---

### Post by gandaran on 2012-01-02
> I have Ubuntu 10.04 in 32 bit machine with Firefox 3.6.24 for Ubuntu. I cannot see some videos and get a message to upgrade Flash player
either you haven't applied the system updates or you have a manually installed old flash plugin you have forgotten where it is installed.

---

### Post by janetk on 2012-01-02
Well Flipper T, your question was a lucky one for me. I went to find the file name of a couple of you tube videos I couldn't see. They had been sent to me on Facebook. As I wanted the actual site name I clicked on the name rather than the arrow on the thumb nail picture. I got the video. I tried it with the others. Click arrow and I get update demand, click file description and get video. I am going to check the other place where I am have video problems (ad.paper.li) but it is not exactly the same symptoms. 
Thank you all - I think I am OK. If not I will start a new thread with new info and question. 
This is a great forum - good help and quickly.

---

### Post by lunalui on 2012-10-11
just wanted to say thanks for this! I've been having problems playing videos posted on facebook for ages. I just got a message asking to upgrade flash player, although the most recent version was installed and I had no problem watching them on youtube, vimeo, etc...
I'm not sure if it was the purge and reinstallation or the flash-aid that fixed it, but I'm really happy everything works again now! :D

---

### Post by SantaFe on 2012-10-11
Not wanting to DeRail the thread, but where IS this plugins folder?  I'm running Firefox 16.0.1 and in my .mozilla folder I have 3 folders: extensions, firefox & seamonkey.  And none of them have a plugins folder either.

---

### Post by sammiev on 2012-10-11
> **SantaFe said:**
> Not wanting to DeRail the thread, but where IS this plugins folder?  I'm running Firefox 16.0.1 and in my .mozilla folder I have 3 folders: extensions, firefox & seamonkey.  And none of them have a plugins folder either.

Click on FF main tab and select Add-ons.

---

### Post by sammiev on 2012-10-11
> **SantaFe said:**
> Not wanting to DeRail the thread, but where IS this plugins folder?  I'm running Firefox 16.0.1 and in my .mozilla folder I have 3 folders: extensions, firefox & seamonkey.  And none of them have a plugins folder either.

Maybe this is what you were looking for.

---

### Post by SantaFe on 2012-10-12
> **sammiev said:**
> Maybe this is what you were looking for.I have it in the /usr/lib/mozilla/plugin folder, I thought he was talking about the .mozilla folder in the home directory. ;)

Funny thing is in my case, even though both the Adobe Flash site & Xubuntu 12.04 BOTH say I have the latest Flash player:
```
santafe@*******-1745:~$ dpkg -l | grep -i flash
ii  adobe-flash-properties-gtk                    11.2.202.243-0precise1                  GTK+ control panel for Adobe Flash Player plugin version 11
ii  adobe-flashplugin                             11.2.202.243-0precise1                  Adobe Flash Player plugin version 11
rc  browser-plugin-gnash                          0.8.10-5ubuntu1                         GNU Shockwave Flash (SWF) player - Plugin for Mozilla and derivatives
rc  flashplugin-installer                         11.2.202.243ubuntu0.12.04.1             Adobe Flash Player plugin installer
santafe@*******-1745:~$ 

```
Firefox keeps telling me I have 11.2 r202 & check plugins always tels me I have a older Flash plugin & when I click to update it, it takes me to the download page offering 11.2.202.243-0precise1 :p

It's like Firefox wants to believe I have an older flash, when I don't. :lolflag:

---

