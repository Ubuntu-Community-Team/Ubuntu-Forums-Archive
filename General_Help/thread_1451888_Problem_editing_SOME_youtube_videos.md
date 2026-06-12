---
title: "Problem editing SOME youtube videos"
date: 2010-04-11
forum: General Help
---

### Post by MuTako on 2010-04-11
Hello everybody!
I've just installed (for couple of hours) ubuntu 9.10, but I have a problem...

I CAN play all the videos, but some of the vid's on Youtube I just can't edit... I mean, that I can't resize, adjust volume, move forward/backward and with others I can do that all. I just don't know what's the difference between them. I have Adobe Flash 10 installed. 
Example:
[This is working just fine]("http://www.youtube.com/watch?v=WoNiZhAUWcg&playnext_from=TL&videos=zGmP3v1nLsM&feature=featured")
[And that one I just can't edit ]("http://www.youtube.com/watch?v=crXaLu9Ecmg&playnext_from=TL&videos=VOE-O94DQJM&feature=featured")

---

### Post by lovinglinux on 2010-04-11
If you have a 64bit system, then install the 64bit version of flash.

See the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by MuTako on 2010-04-11
THanks, but...
_**[Here]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2")**_ it says: 
"First make sure you have the proprietary graphics card driver installed. Go to “System >> Administration >> Hardware Drivers” and enable the corresponding driver."
   but when I go to Hardware Drivers - there is nothing there! What should I do? I don't even know what's my video card and how can I see it here in ubuntu ?

Anyways, I made that:
I installed **_[That one]("http://ubuntuforums.org/showthread.php?t=1414595")_** first, then tried:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```...but nothing has changed.
Then I tried to install '         APT for Ubuntu 9.04+' from Adobe's site, but it's telling me: "Could not find package 'adobe-flashplugin' " ... 
Any further ideas? Sorry for my newbie answers/questions, but... :confused:

---

### Post by WinterRain on 2010-04-11
[Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") is the 64bit flash plugin. Put it on your desktop. Right click it and **extract here**. Then open a terminal (Ctrl+Alt+T) and do: (copy and paste code below into terminal, hit enter, then password, then enter. Done)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox if open. Easy.

---

### Post by gordintoronto on 2010-04-11
> **MuTako said:**
>    but when I go to Hardware Drivers - there is nothing there! What should I do? I don't even know what's my video card and how can I see it here in ubuntu ?


Open Accessories/terminal and enter the command:
lspci

You should get about 20 lines of ouput.  One of them will say, "VGA compatible controller," and it will identify your video card.

---

