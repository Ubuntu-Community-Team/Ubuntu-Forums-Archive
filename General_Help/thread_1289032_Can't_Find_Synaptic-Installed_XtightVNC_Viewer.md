---
title: "Can't Find Synaptic-Installed XtightVNC Viewer"
date: 2009-10-12
forum: General Help
---

### Post by Zoandar on 2009-10-12
I have just used the Synaptic Package Mgr. to install Xtightvnc viewer (and 2 others as well) and I cannot find where the listing is to start Xtight (or the other 2). It isn't in the Applications list and I can't find it anywhere in administration or preferences either. 

How does one execute Xtightvnc viewer (or the other 2 installed viewers)?

---

### Post by Dejai on 2009-10-12
Open a terminal and type:
xtightvncviewer &

If it says thats not installed type:
sudo apt-get install xtightvncviewer

If you don't want to use terminal all the time right click on your desktop and make a link and type that command in then you can just click that and it will open. :)

---

### Post by Zoandar on 2009-10-12
Thanks a lot! I would not have figured that out!!! Is it normal to require this action to execute anything installed with Synaptic Pkg. Mgr.? Applications I have installed with Add/Remove end up in the Applications list.

Your suggestion works just fine from Terminal, but my desktop launcher I made as you suggested won't do anything. 

Would you happen to know of any VNC viewers I can run here on Ubuntu that will let me scale the size of the Windows PC desktop here on the notebook running Ubuntu? (Like LogMeIn can do). I see xtightvnc viewer doesn't have that feature either. 

Thanks!

Zoandar

---

### Post by Dejai on 2009-10-12
Try:
rdesktop

---

### Post by Zoandar on 2009-10-12
rdesktop appears to be a text-only program or something. All I ever see when I try to run it is a listing of the command modifiers. I tried using:

rdesktop& -d<VNC Server's IP address> -u<my username> -p-

to get it to work.

But that doesn't work. There are a great many parameters shown for rdesktop. I could use a suggestion for the correct command line entries.

---

### Post by Zoandar on 2009-10-12
I found a graphical version of rdesktop and got that installed. But I can't use it. It won't connect for me to the RealVNC server on my windows PC like several other (tightvncviewer and others) viewers will (which don't have resizable desktop views). So I looked into why. It seems that it is a version of Remote Desktop, which Microshoft cleverly originally included, but later disabled, in Windows XP Home. You must have Windows XP Pro to activate it in Windows XP. 

For now I am using TightVNC on Windows and its viewer on Ubuntu, but I still don't have any way to reduce the size of my wide-screen displays on the Windows PC to make them comfortably viewable from Ubuntu. If anyone has any other VNC suggestions, or ever figured out how to make LogMeIn FREE work from Ubuntu 9.04, please let me know. Their Firefox broswer plugin just crashes Firefox from Ubuntu. 

Zoandar

---

