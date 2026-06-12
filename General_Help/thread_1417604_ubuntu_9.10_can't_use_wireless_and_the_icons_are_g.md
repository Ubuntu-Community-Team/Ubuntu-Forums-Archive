---
title: "ubuntu 9.10 can't use wireless and the icons are gone from the top right"
date: 2010-02-27
forum: General Help
---

### Post by hunterkasy on 2010-02-27
first off I am running Ubuntu 9.10 on a Dell Inspiron 600m 
Kernel Linux: 2.6.31-19 generic
gnome: 2.28.1

I don't know when the problem started (not my computer) the first problem I heard was not able to get on the Internet, using wireless.  but I am able to connect to the Internet using a wired connection. then the icons on the top right of the screen disappeared all that is displayed now is name, and if you click on the name if gives you the shut-down menu and the time and date, it does not show the battery or the Ethernet or wireless connection  
all available updates are installed

please let me know if you need more info I don't know what else to say

---

### Post by johngreth on 2010-02-27
You should be able to bring back the network/power/sound things by right clicking the top bar and clicking "add to panel", then add "Notification Area".

---

### Post by hunterkasy on 2010-02-28
> **johngreth said:**
> You should be able to bring back the network/power/sound things by right clicking the top bar and clicking "add to panel", then add "Notification Area".

I added the notification area to the panel, still nothing is showing, and my wireless is still not working

---

### Post by garvinrick4 on 2010-02-28
If all the notification area applets are gone and the seperater (3 dots) then I would have to
say to purge and reinstall that program. Make sure you do a "sudo apt-get clean" so you get a new one instead of old one from your cache. without quotes. Can never hurt to start at the beginning when trying to figure one out.

---

### Post by hunterkasy on 2010-02-28
> **garvinrick4 said:**
> If all the notification area applets are gone and the seperater (3 dots) then I would have to
say to purge and reinstall that program. Make sure you do a "sudo apt-get clean" so you get a new one instead of old one from your cache. without quotes. Can never hurt to start at the beginning when trying to figure one out.

I don't understand what you are talking about, "reinstall that program" 

this labtop is my 2 Nephews and 1 niece oldest 10 youngest is 4.  the only thing they do is play some online games and the games I installed from the add/remove.  everything was working just fine on this labtop until a couple of days ago, they were unable to get on the Internet they connect to the router by wireless, I was able to connect to the Internet by Ethernet cable I also noticed the icons on the top left were gone like the battery, network connection, speaker, and what else is their by a standard install 
I was able to install the notification area by right clicking and go to add to panel.  now their is 3 dots stacked by the date.  when I right click and go to add to panel, what is missing is not in the list of things to add.

---

### Post by garvinrick4 on 2010-02-28
What is missing network manager?

---

### Post by 3rdalbum on 2010-02-28
Hit Alt-F2 and type:

```
nm-applet
```

---

### Post by garvinrick4 on 2010-03-01
> **hunterkasy said:**
> I don't understand what you are talking about, "reinstall that program" 

this labtop is my 2 Nephews and 1 niece oldest 10 youngest is 4.  the only thing they do is play some online games and the games I installed from the add/remove.  everything was working just fine on this labtop until a couple of days ago, they were unable to get on the Internet they connect to the router by wireless, I was able to connect to the Internet by Ethernet cable I also noticed the icons on the top left were gone like the battery, network connection, speaker, and what else is their by a standard install 
I was able to install the notification area by right clicking and go to add to panel.  now their is 3 dots stacked by the date.  when I right click and go to add to panel, what is missing is not in the list of things to add.

In ubuntu software center the network manager applet is what I meant, should have been specific. Notification area is the 3 dots. It is the applets I know the kids need like now. I have had to goof with in Lucid Lynx but not Karmic. Kids can be rough on a machine so see if the 3 or so applets can be removed and cleaned from system and installed again. Standard install they are usually on top right next to date are they not.
three applets usually are installed with notification (3 dots) I think they are hidden on left somewhere, if you install twice you just get the 3 dots of notification area. So the kids have moved originals over to left and something is a miss. Just a opinion.

---

### Post by nightwolf2k5 on 2010-03-01
When you get to the login screen. At the bottom make sure your session is set to Gnome. Once it is set to Gnome, add the notification area to the panel.

Sometimes, if the session is set to Failsafe Gnome, adding the notification area doesn't seem to help.

Else.. this [http://ubuntuforums.org/showthread.php?t=1311790&page=2](http://ubuntuforums.org/showthread.php?t=1311790&page=2) could help.

---

### Post by hunterkasy on 2010-03-01
> **nightwolf2k5 said:**
> When you get to the login screen. At the bottom make sure your session is set to Gnome. Once it is set to Gnome, add the notification area to the panel.

Sometimes, if the session is set to Failsafe Gnome, adding the notification area doesn't seem to help.

Else.. this [http://ubuntuforums.org/showthread.php?t=1311790&page=2](http://ubuntuforums.org/showthread.php?t=1311790&page=2) could help.

I got it fixed, it was set to fail safe, I changed it back to gnome now the icons are their, it is picking up a wireless signal, 

BTW, is their anyway to lock down the computer so no one can make any changes to it? I want them to be able to do their homework, online games, and installed games.  but It would be nice if I could prevent them from making any changes that could affect the computer

---

### Post by johngreth on 2010-03-01
> BTW, is their anyway to lock down the computer so no one can make any changes to it? I want them to be able to do their homework, online games, and installed games. but It would be nice if I could prevent them from making any changes that could affect the computer

Go to System->Administration->Users and Groups.
click the key button and type password.
Click a user and hit properties.
Then hit the user privileges tab.
You can disable a lot of things that may be system compromising.

---

