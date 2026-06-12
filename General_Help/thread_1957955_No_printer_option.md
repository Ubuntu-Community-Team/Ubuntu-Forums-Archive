---
title: "No printer option"
date: 2012-04-13
forum: General Help
---

### Post by soakes94 on 2012-04-13
I am running Ubuntu Server 10.04, I have installed gnome and vncserver so I can work with the server from any device. I'm trying to setup CUP's and then an air print server and share them to all my linuux, windows and apple devices. However I cant install my printer as there is no printer option under System > Administration or System > Prefernces. I have tried right clicking on system and checking there for the printer but there is nothing. Its like it hasnt installed? Anyone got any ideas?

Thanks

---

### Post by abyrne on 2012-04-13
First off, Welcome to the Forums!

What packages did you install to install GNOME? Did you use
```
sudo apt-get install ubuntu-desktop
```
or something else?

Also, when setting up any kind of server, it usually isn't best practice to install a GUI on top of it, mainly for security and performance reasons. If you're not planning on opening up the server to the Internet (ex. Web Server), then you don't have too much to worry about. Otherwise, It might help to become fluent in command line and use SSH instead.

---

### Post by soakes94 on 2012-04-13
I used 

```
sudo apt-get install gnome-core
```

followed by 

```
sudo apt-get install vnc4server
```

Its just for home use, runs my DHCP, DNS and hopefully printer services. I might install a firewall or something just to protect the network or something like that, maybe peerguardian.

Cheers

---

### Post by abyrne on 2012-04-13
Ok, thanks for the info. Just installing gnome-core doesn't install anything but the bare minimum for running a GUI. That means that CUPS probably isn't even installed on your system. Run
```
sudo apt-get install cups system-config-printer-gnome
```
That should do it

---

### Post by soakes94 on 2012-04-13
Perfect! It worked :) I had installed cups and had the web interface running but I couldnt get anything to work on my servers GUI.

Cheers :)

---

