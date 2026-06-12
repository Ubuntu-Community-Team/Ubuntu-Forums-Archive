---
title: "Repairing broken packages without internet"
date: 2010-05-13
forum: General Help
---

### Post by Jesdisciple on 2010-05-13
I forgot that Python is actually essential to Gnome and wanted to update to 3.1, and didn't realize my mistake until some of Gnome had been removed, then I Ctrl+C'd out. Now I can't even connect to the internet to repair my broken packages. I'm out of town for Mother's Day, but in the car it occured to me that I should have tried my Live CD. Does anyone have another suggestion?

As a side issue, is it alright to install more than one version of Python? I'm guessing so, so long as I keep track of which one I'm calling.

I used apt-cdrom to update my sources.list appropriately so I could apt-get from the Live CD, but apt complained about locales.  Now sources.list has strangely lost the cdrom line, but I'll put it back when I next boot to repair mode.

*Sigh*...  Help, please?

---

### Post by Jesdisciple on 2010-05-14
Wow this got buried fast... (bump)

---

### Post by nothingspecial on 2010-05-14
Option one -


get a wired connection and log in to recovery mode.
```

sudo ifconfg eth0 up
sudo dhclient
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by Jesdisciple on 2010-05-16
Alright, I finally got this done.  Sorry it took so long.

I saved the provided bash commands at the root of the broken partition from the Live CD, then booted into repair mode and ran them.  At first I didn't think to redirect and then I got the syntax wrong, but here is the output of the file once I did redirect it correctly...

(In case it matters, I'm running Karmic but sources.list has several Jaunty lines in it.)

```
There is already a pid file /var/run/dhclient.pid with pid 6960
removed stale PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:51:d1:a5
Sending on   LPF/eth0/00:1b:24:51:d1:a5
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.69 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.69 from 192.168.1.254
bound to 192.168.1.69 -- renewal in 34223 seconds.
Hit http://security.ubuntu.com jaunty-security Release.gpg
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Hit http://security.ubuntu.com jaunty-security Release
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: indicator-applet-session but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
E: Broken packages
```Erm... I don't suppose there's an option two?

Thanks. :)

---

### Post by nothingspecial on 2010-05-17
In recovery mode again

```
sudo apt-get install -f
```

Then try to install ubuntu-desktop again.

---

### Post by Jesdisciple on 2010-05-21
Bash script:```
sudo apt-get install -f
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

Output:```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 947 not upgraded.
Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Get:2 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com jaunty-security Release [57.9kB]
Hit http://us.archive.ubuntu.com jaunty Release
Get:4 http://us.archive.ubuntu.com jaunty-updates Release [57.9kB]
Get:5 http://security.ubuntu.com jaunty-security/main Packages [157kB]
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Get:6 http://us.archive.ubuntu.com jaunty-updates/main Packages [238kB]
Get:7 http://security.ubuntu.com jaunty-security/restricted Packages [2612B]
Get:8 http://security.ubuntu.com jaunty-security/main Sources [42.2kB]
Get:9 http://security.ubuntu.com jaunty-security/restricted Sources [617B]
Get:10 http://security.ubuntu.com jaunty-security/universe Packages [88.3kB]
Get:11 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [2612B]
Get:12 http://us.archive.ubuntu.com jaunty-updates/main Sources [67.8kB]
Get:13 http://security.ubuntu.com jaunty-security/universe Sources [22.5kB]
Get:14 http://security.ubuntu.com jaunty-security/multiverse Packages [1669B]
Get:15 http://security.ubuntu.com jaunty-security/multiverse Sources [580B]
Get:16 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [617B]
Get:17 http://us.archive.ubuntu.com jaunty-updates/universe Packages [118kB]
Get:18 http://us.archive.ubuntu.com jaunty-updates/universe Sources [33.1kB]
Get:19 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [9311B]
Get:20 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [3288B]
Fetched 904kB in 6s (133kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: indicator-applet-session but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
E: Broken packages
```

---

### Post by Jesdisciple on 2010-05-22
(bump)

---

### Post by Jesdisciple on 2010-05-24
(bump)

---

### Post by Jesdisciple on 2010-05-26
(bump)

---

### Post by Jesdisciple on 2010-06-03
Is there no other possible lead to fixing this?

---

