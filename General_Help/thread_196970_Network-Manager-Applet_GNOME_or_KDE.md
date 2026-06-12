---
title: "Network-Manager-Applet: GNOME or KDE?"
date: 2006-06-15
forum: General Help
---

### Post by rverrips on 2006-06-15
Hiyee

I've been doing a fresh install of version 6.06 of Ubuntu, Kubuntu and Xubuntu every other day to try establish the best "out-of-the-box" experience for mass-deployment on a number of laptops.  

So far the Xubuntu/XFCE4 set of apps seems to support the hardware best upon initial install and the default apps (in particular thunderbird for mail) works best with the courier IMAP server I need to connect to.

Anyway, I'd like the Network Manager Panel Applet which worked great in both Gnome and KDE, and I'd like to install it under XFCE4.  However both the network-manager-gnome and knetworkmanager packages have a whole set of extra lib dependancies (19 for G and 21 for K)

Double barrelled question:   Is there an XFCE4 panel version of network-manager applet?  
Or, is there any (or what is) the difference between the KDE and Gnome version?

Thanks

Yours

Roy 

:confused:

---

### Post by dom on 2006-09-20
> **rverrips said:**
> Hiyee

Double barrelled question:   Is there an XFCE4 panel version of network-manager applet?  
Or, is there any (or what is) the difference between the KDE and Gnome version?


I think the applet is only a front end for a daemon, so it's no biggy perhaps.

I just posted in another thread which described how to get this working in Xubuntu by starting some gnome services etc.

Sounded great on paper, but it didnt' work for me. Well, let me clarify, the nm-applet (gnome version) shows up, but it doesnt show any network interfaces. The icon has a red 'x' over it.

It also reports "No Network Connection", even though here I am with wired and wireless interfaces both working away happily !

Lets see if anybody has the solution.

---

### Post by Philip g on 2006-09-29
In reply to dom, I found that the network manager and hence it's applets wouldn't function properly until I followed the advise found in:-

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

on editing:-

/etc/network/interfaces

essentially 'hashing' out all references to interfaces except lo

this worked a treat for me.

Hope this helps.

---

### Post by orb9220 on 2006-09-29
Yes as stated by Philip g that is what I did to get it working.
Now the weird thing is when I run it on xfce startup I get 3 nm-applets running  in notification tray. And had to right click delete two of them.

Do not know if this has been fixed in xfce4 or not.

---

### Post by dom on 2006-10-10
I have been using Wifi Radar the last few weeks and am very very happy with it from what i've seen to date. I've also install the 'ConnSets' firefox plugin to help deal quicker with the proxy/cache issues when moving between internet connections.

---

