---
title: "Magic spell req'd to re-appear Network Manager icon from top bar"
date: 2010-07-08
forum: General Help
---

### Post by edanto on 2010-07-08
The small icon from the top bar which allows me to choose which network I connect to, as has a bluetooth icon that was there. 

I don't know how it's gone but I've had no success in making it re-appear.  Is there something that I could put into a terminal (i.e. a magic spell!) that would make it re-appear, please?

---

### Post by nothingspecial on 2010-07-08
You just need to right click the panel, choose add to panel then choose notification area or indicator applet or which ever one it is. Try them both.

---

### Post by ajgreeny on 2010-07-08
It's the notification area, at the moment.  There is a general move in gnome, not just ubuntu, to take all those things from the NA and put them into Indicator applet, so it may not stay that way in future.

---

### Post by edanto on 2010-07-08
Thanks guys. When I try that, something small is added to the Top Panel, but it's only a wee | of dotted lines, there's no sign of that wireless icon that was there. (like .cC sideways)

I must be missing something really simple!  

It's certainly connected OK to the wireless, I'm on my home network now.

---

### Post by nothingspecial on 2010-07-08
move it a bit

---

### Post by edanto on 2010-07-08
:redface:

nope, nothing.  There are three of those wee pipes now and when I move them a few cm left and right I don't see anything. 

This is the stuff I've been trying earlier, it's reassuring to know that I was headed in the right direction at least.  continued thanks!

---

### Post by edanto on 2010-07-09
Any suggestions guys, please?

---

### Post by edanto on 2010-07-20
Still no joy.

Is there any other way to access the Network Manager dialogue?  When I go to System | Preferences | Network Connections, I just see the list of wirelesses that I have been connected to, not the list of ones that I could connect to.

Anyone?

---

### Post by nothingspecial on 2010-07-20
You could try installing wicd (an alternative network manager)

---

### Post by Aisteru on 2010-07-29
If you cannot find nm-applet on the list of running processes, go to the list of startup applications (system>preferences>startup applications), make sure it is on the list & that the box next to it is checked. If it is not on the list, click "add." in the command box put "nm-applet --sm-disable," then pick a name, etc.


Hope this helps.

---

### Post by edanto on 2010-08-14
Thanks for the replies guys - I didn't have the thread set to notify me, so unfortunately I'm only seeing them now!

Aisteru -  I had a look at the list of start up applications and the Network Manager is there, so at least I know that it's running.

Is there something that I can put in a terminal to open up the nm-applet?

EDIT-

Hah! When I put nm-applet --sm-disable into a terminal, then the icon appears at the top of the screen!!

This is what comes up in the terminal in case it means anything to anyone...

(nm-applet:2749): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(nm-applet:2749): atk-bridge-WARNING **: IOR not set.

(nm-applet:2749): atk-bridge-WARNING **: Could not locate registry
** (nm-applet:2749): DEBUG: old state indicates that this was not a disconnect 0

This will give me a workaround for when I need to connect to new networks - but  I really would like to figure out how to get that icon permanently back in the top bar. 

Thanks for the help so far!

---

