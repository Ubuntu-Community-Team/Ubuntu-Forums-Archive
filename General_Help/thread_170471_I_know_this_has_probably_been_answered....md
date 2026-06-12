---
title: "I know this has probably been answered..."
date: 2006-05-04
forum: General Help
---

### Post by chrisadatl on 2006-05-04
I have a winxp box, a backtrack (linux) box and a Ubuntu box.

I can remote desktop from the backtrack box, and the ubuntu box into my xp box.

I cant remote from my xp box to either of the other linux boxes.

I cant remote from my linux  into another linux box.

I hear talk about VNC. I am not sure what it is. I would like to know if this application will allow my xp box, to take desktop control of my linux boxes.

the goal is to take the head off my ubuntu and have it singing along with the win2k server box that is also headless. I want to expeirement with both of the web services.. so forth and so on...

Can anyone, who has the time and is willing to help someone who is trying to get out of Windopes,  explain to me in caveman terms, how do I remote desktop either one of my linux boxes from an xp box...

any help would be greatly appreciated as i have exhausted all of my braincells and have nothing left in life to look forward to other then playing in traffic.


thanks.
SA

---

### Post by louis_nichols on 2006-05-04
Yes, VNC is an app that will let you do what you wish. You'll basically just have a window that reproduces your Linux desktop. It is completely cross-platform. Just install vncserver in Linux and a vnc viewer in windows ([realvnc ]("http://www.realvnc.com/download.html")or [tightvnc]("http://www.tightvnc.com/") or [UltraVNC]("http://ultravnc.sourceforge.net/") - the latter would be my personal recommendation).


After this, you start your vncserver in Ubuntu. I am not near my Ubuntu setup right now, so I can't give you detailed description how, but I'm pretty sure there's a GUI that will let you easily do this. Starting it from the command line isn't difficult either.

Then, start your viewer in windows and connect to: xxx.xxx.xxx.xxx:0 where the x's are the IP of the machine running the server. It can also be an internet adress.

---

### Post by chrisadatl on 2006-05-04
I have installed tight vnc on my xp box and attempted the connection to my ubuntu server and it worked! i guess ubuntu has it installed...

I really appreciate the help,

is there a way that i can initiate the desktop connection to ubuntu and not have it prompt permission to take control? this means that i still need the monitor on it to answer to the request..

I would like to be able to launch it and not have to give permission on the server ...

ANy help is greatly appreciated...

SA

---

### Post by louis_nichols on 2006-05-05
sure there is a way! I just don't know it, yet! :)

try ```
man vncserver
``` to see the documentation. It will display all options for starting the server.

also ```
vncserver --help
``` should display a shortened version of available options

---

