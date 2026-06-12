---
title: "WICD and BAD PASSWORD"
date: 2010-12-21
forum: General Help
---

### Post by gdiloren on 2010-12-21
I'm entering the right paraphrase, it works with network manager but I can't connect with wicd, it keeps telling me it is a bad password. I use WPA2 personal encryption

---

### Post by sir_robert007 on 2010-12-21
> **gdiloren said:**
> I'm entering the right paraphrase, it works with network manager but I can't connect with wicd, it keeps telling me it is a bad password. I use WPA2 personal encryption

Yeah ive been having this same problem although with me it happens intermittently. Sometimes it works sometimes it doesnt.

---

### Post by claracc on 2010-12-21
This problem can have three different solutions.

1.- If you use a wired connection, you edit the file /etc/wicd/wired-settings.conf (with sudo gedit), and look at the end of the file, if there is a line with [ ], you delete it. Then start the daemon: sudo /etc/init.d/wicd start or /etc/rc.d/wicd start

2.- edit /etc/init/networking.conf (with sudo gedit), at the end, add line exec wicd, then start the daemon:wicd-client. This was the solution that worked for me as I have a wireless connection.

3.- The script to start wicd is not valid, so I recommend to download the deb package of wicd, open it with file manager and copy the file /etc/init.d/wicd to the hard drive

---

### Post by gdiloren on 2010-12-21
I Googled wicd bad password and found out there may be a problem with network manager interfering with wicd when you have it on the same Linux PC. I kept it just in case, May be that's why. Now I'm on internet with Network Manager and it's been more than an hour but I had trouble connecting to the router and staying connected at the beginning after I started up my PC. 
   What I want to know is: Is there improvement connecting with wicd or is it the same thing? Does it stays connected longer? Why installing it through Software Center is prohibited while using Synaptic Manager you just can install it?

---

### Post by QLee on 2010-12-21
[QUOTE=gdiloren]... Why installing it through Software Center is prohibited while using Synaptic Manager you just can install it?[/QUOTE]

Well, you shouldn't be able to install wicd with Synaptic on a system that has network manager because of the conflict, installing wicd should cause Synaptic to remove network-manager and network-manager-gnome. At least that's the way it has worked up to now, are you using 10.10 and have things changed?

Edit: I just checked and I see I was wrong, things have changed. Sorry for the noise.

---

### Post by gdiloren on 2010-12-22
> **QLee said:**
> Well, you shouldn't be able to install wicd with Synaptic on a system that has network manager because of the conflict, installing wicd should cause Synaptic to remove network-manager and network-manager-gnome. At least that's the way it has worked up to now, are you using 10.10 and have things changed?

Edit: I just checked and I see I was wrong, things have changed. Sorry for the noise.
In maverick, wicd installs without uninstalling network manager. It works with wired connection but is useless for wireless connection because of bad password issue. Removing completely network manager could end up losing any interface for internet connection and a complete reinstall of Maverick. So I guess wicd is not a good alternative to network manager for wireless!

---

