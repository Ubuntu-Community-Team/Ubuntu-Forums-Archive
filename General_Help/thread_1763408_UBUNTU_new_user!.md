---
title: "UBUNTU new user!"
date: 2011-05-20
forum: General Help
---

### Post by mffaswan on 2011-05-20
hello there,

this is my first time to use this OS "Ubuntu", I downloaded the file (natty-desktop-i386.iso), and installed it to my USB drive.

after extracting to the USB Flash Drive, I rebooted the laptop from the usb, it worked OK, after that, i could connect automatically to the wifi router and had Internet connection, but it keep cutting and reconnect each 3 or 4 min, and i can't save the router's password, i need to re-write it each time!

also, i could not run most of my MP3, AVI, Xvid, etc multimedia files stored on my pc. it says that plugins are missing!

also i need to know the Switching keys from English language to Arabic language on keyboard to be able to write in Arabic language.

is there any tutorial videos or documents for the basics of UBUNTU?? any links??

thanks :)

---

### Post by webofunni on 2011-05-20
You need to install the codecs to play mp3/avi formats. otherwise install vlc or mplayer. 

Do ALT+F2 and type gnome-terminal. In that execute following command

```
sudo apt-get install vlc
```

That will install vlc and you can play videos or music with that. 

You can change keyboard layout in "System -> preference -> keyboard" or do

ALT+F2 and type gnome-keyboard-properties. You can change the layout there.

---

### Post by krishnandu.sarkar on 2011-05-20
Go to terminal and enter...

```
sudo apt-get install ubuntu-restricted-extras
```It'll install basic packages that one needs in daily life.

---

### Post by mffaswan on 2011-05-20
> **webofunni said:**
> You need to install the codecs to play mp3/avi formats. otherwise install vlc or mplayer. 

Do ALT+F2 and type gnome-terminal. In that execute following command

```
sudo apt-get install vlc
```That will install vlc and you can play videos or music with that. 

You can change keyboard layout in "System -> preference -> keyboard" or do

ALT+F2 and type gnome-keyboard-properties. You can change the layout there.





thanks friend for reply,

I got the following:

mohamd@ubuntu:~$ sudo apt-get install vlc
[sudo] password for mohamd: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mohamd@ubuntu:~$ 

the install is not starting after the above msg :(

---

### Post by Vaphell on 2011-05-20
it says that most likely you have package manager/software center open. Only 1 program at a time can manage packages.

**sudo apt-get install <package name>** is equivalent to selecting <package name> in synaptic package manager and applying changes, if you prefer graphical way.

---

### Post by mffaswan on 2011-05-20
i think i need to read more about this OS!

i think i am lost in this UBUNDU :(

is there any videos or pdf for ubundu for starters??

---

### Post by webofunni on 2011-05-20
There are official doc on ubuntu. You can find that at [https://help.ubuntu.com/](https://help.ubuntu.com/) . I guess it will be easy for you to use the Graphical application to install vlc. 

[https://help.ubuntu.com/11.04/software-center/C/installing.html](https://help.ubuntu.com/11.04/software-center/C/installing.html)

In the software center search for vlc and install it as mentioned in above link. Which version of ubuntu you are using ?

---

### Post by grahammechanical on 2011-05-20
Try pressing F1. That will bring up a help document that explains the desktop.

try this link

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

regards.

---

### Post by mffaswan on 2011-05-20
thank u my friends for the gr8 help :)

will try to find my way through it

---

