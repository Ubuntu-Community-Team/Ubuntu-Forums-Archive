---
title: "ushare configuration"
date: 2010-05-25
forum: General Help
---

### Post by PhoenixDream on 2010-05-25
Hi, Im having trouble with ushare, especially with the adding of my media directory path in /etc/ushare.conf 
All my media is located on a secondary hard drive which I have named 'Abyss' and on the hard drive I have 2 folders 'My Music' and 'My Videos' which I want to share via streaming to my 360. 
What is the proper directory path to put into the .conf file when using gedit?

Cheers!

Update:
I have sorted the above problem out but have discovered a new one, this is the output I receive from starting ushare in terminal:

hordak@hordak-desktop:~$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.101:49204
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/Abyss
Found 39245 files and subdirectories.


Apparently my eth0 is down?

---

