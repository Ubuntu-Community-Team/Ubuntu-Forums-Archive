---
title: "Remote Desktop to Windows"
date: 2010-09-10
forum: General Help
---

### Post by astroidea on 2010-09-10
I'm having trouble getting it to work. 
I followed this guide
[http://www.goitexpert.com/en/index.cfm/2007/3/2/Remoting-into-a-Windows-machine-from-Ubuntu/](http://www.goitexpert.com/en/index.cfm/2007/3/2/Remoting-into-a-Windows-machine-from-Ubuntu/)

When I try to connect, it says 
ERROR: Failed to open display 

I did some more googling and the consensus seems that the error message comes up if I don't have the x-window system. I'm using ubuntu netbook 10.04. Does it have it?

---

### Post by astroidea on 2010-09-10
OK I think I found out that I need X11 for it to work, and I found the apt-get for it.
I tried 
sudo apt-get install x11-common

It says I already have the latest version installed. What's goin on?

---

### Post by silverglade00 on 2010-09-10
Those are some archaic instructions. Install gnome-rdp and set up your Windows machine's ip address and your user name. Works great!

---

### Post by astroidea on 2010-09-10
Cool Gnome-RDP looks like a nice gui program I was looking for that could use MS' RDP without me needing to install anything on the server side, but it seems to not be liking me. 
When I try to open it, it says Opening Gnome-RDP for a few seconds, then  the message goes away, the mouse stays on the loading cursor for a few  seconds, and then it goes back to normal and nothing happens. 
I installed the one from sourceforge. wat do?

---

### Post by silverglade00 on 2010-09-10
Gnome-RDP is right in the Ubuntu repo. 
```
sudo apt-get install gnome-rdp
``` That command will install it for you. You should get rid of the Sourceforge one. Also, when it loads, it might go straight to the notification area by the clock.

---

### Post by astroidea on 2010-09-10
Thanks for the quick reply.
I actually tried that first before I went to sourceforge. It says the package cannot be found.
I tried looking for any icons that popped up on the taskbar either and I don't see any.

---

### Post by silverglade00 on 2010-09-10
Do you have the Universe repo enabled? Go to System - Administration - Software Sources. Make sure it is enabled. Also, which version of Ubuntu are you using?

---

### Post by astroidea on 2010-09-10
Sweet. Movin along here, but not quite there yet. The universe wasn't checked. I have it on default settings on however it loaded from the usb flash. So I deleted the old gnome-rdp using sudo apt-get remove gnome-rdp and  reinstalled using your command line.The apt-get now worked and gnome-rdp starts right up, although it gives me a bunch of error messages and closes. 
First it says:
Error in query: 
SELECT * FROM version WHERE id = 1
Error: no such table version

second it says:
There was an error during the reading of record.

third it says:
Invalid database version!

---

### Post by silverglade00 on 2010-09-10
Go into your home folder and press CTRL-H to show hidden files. Delete .gnome-rdp.db and restart Gnome-RDP. That should fix it.

Command line way (be very careful with this one. rm is POWERFUL):
```
rm -f ~/.gnome-rdp.db
```

---

### Post by astroidea on 2010-09-10
Wow that did the trick, thanks!

This RDP is still quite a bit slower than the windows one. Oh well, at least it works.

---

