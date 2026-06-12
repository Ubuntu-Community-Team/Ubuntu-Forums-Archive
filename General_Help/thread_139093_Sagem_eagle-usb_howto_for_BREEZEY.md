---
title: "Sagem eagle-usb howto for BREEZEY"
date: 2006-03-03
forum: General Help
---

### Post by jerrykenny on 2006-03-03
Hi folks,

A lot of us have been round in circles with this one, and I've done this in such a roundabout way, however I think I can summarise howto connect this damn thing to Breezey . . . . NB, you'll save a lot of time if you can have a working ethernet connection to acheive this in the first place . . . . otherwise you might be searching around for dependencies and burning to disks etc

This is pretty much how I did it, but it seems to be a very idiosyncratic thing , however it is working . . . .


If its a fresh install, and you've no access to the internet,     <sudo nano /etc/apt/sources.list> and comment out all the natwork repositories . . . . 

[COLOR="Blue"]sudo apt-get install gcc-3.4[/COLOR]

[COLOR="Blue"]sudo apt-get install module-assistant[/COLOR]
[COLOR="Blue"]
sudo module-assistant prepare[/COLOR]

[COLOR="Blue"]sudo module assistant get eagle-usb[/COLOR]
[COLOR="Blue"]
sudo module-assistant build eagle-usb[/COLOR]  (if this stalls, then you probably haven't got gcc-3.4)

. . . . . put your info in now, ie username & password . . . .  but you'll probably have to input the data again for some reason . . . . ?


This creates a .deb file for you, in  /usr/src  (but it doesn,t actually tell you this)


[COLOR="Blue"]sudo dpkg -i  /usr/src/eagle-whatever.deb[/COLOR]  

[COLOR="Blue"]sudo nano /etc/modules [/COLOR]             add the following to this file    [COLOR="Red"] eagle-usb[/COLOR]

now try to reboot, and if you had an ethernet modem or router installed, then unplug it, or ubuntu may be trying to use that as the default interface. . . . . 

[COLOR="Blue"]sudo startadsl   [/COLOR]         (should start the thing) . . . . failing that . . . .  

[COLOR="Blue"]eaglestat [/COLOR]       (will tell you if the thing has even registered) . . . . . if it says modem is operational, and you've still no connection, then maybe you've still got  an ethernet router plugged in, and its trying to connect via this  ? . . . . . if its "waiting", then try

[COLOR="Blue"]sudo eaglectrl -d [/COLOR]     (to give a kick) . . . . then

[COLOR="Blue"]sudo startadsl[/COLOR]

If this still times out after a minute or so, then you can put your details in again with 

[COLOR="Blue"]sudo eagleconfig[/COLOR]      (put in your username again and pawwsord)

[COLOR="Blue"]sudo startadsl[/COLOR]

If you want a button on your panel to start it for you, make a link to a command, which can be [COLOR="Blue"]gtksu startadsl[/COLOR] for gnome users, or[COLOR="Blue"] kdesu startads[/COLOR]l for kde fans

A lot of the problem with the modem seems to be caused by installing eagle-usb-utils BEFORE you've manually installed the .deb file. . . . . . or maybe having another network interface plugged in at the same time . . . ? not too sure, but it would be sensible if your system thought that the the sagem modem would be its VERY LAST RESORT !

If you change ISP, or think you've maybe made a typo while inputing your password or details, then you've two options . . . . 

1) sudo dpkg-reconfigure eagle-usb-utils
2) sudo eagleconfig


Good Luck;)

---

