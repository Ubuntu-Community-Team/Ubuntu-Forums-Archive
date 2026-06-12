---
title: "Unbricking Network Manager"
date: 2011-07-12
forum: General Help
---

### Post by lampak on 2011-07-12
I've had a terribly stupid idea to try compiling Network Manager, Modem Manager and nm-applet from source, following the instructions from [here]("http://projects.gnome.org/NetworkManager/developers/"). Now my networking doesn't work at all and I've got problems going back. 
(this is what happens where you are too stingy on hdd space for a virtual machine)

**Trying to go back:**
I did sudo make uninstall and reinstalled all packages from under network-manager and network-manager-applet from [this PPA]("https://launchpad.net/~network-manager/+archive/trunk") (from a pendrive). Now when I try sudo service network-manager start it tells me the job is already running but it doesn't seem so - ps aux doesn't show it. nm-tool says it can't connect to NetworkManager. 

The applet doesn't display an icon neither. Running it from the terminal indicates it lacks libnm-glib.so.4 file. The libnm-glib package provides only libnm-glib.so.2. But it's the smallest problem. 

**Trying to fix what I've got**
The git version displays the applet icon, NetworkManager appears in the results of ps aux and nm-tool shows my ethernet and wifi cards so staying with this mess seems more promising for now. But it doesn't connect. When I click the applet icon no available wifi networks appear. Trying to connect to my network like to a hidden one fails. 

**[COLOR="Red"]Logging[/COLOR]**
As far as I've managed to google, NetworkManager should log to /var/log/daemon.log. But the log is completely empty and its modification date is in May. I've tried adding a [logging] section to /etc/NetworkManager/NetworkManager.conf according to a man page for the file, so now the file looks like
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[logging]
level = DEBUG
domains = NONE, HW, RFKILL, ETHER, WIFI, BT, MB, DHCP4, DHCP6, PPP, WIFI_SCAN, IP4, IP6, AUTOIP4, DNS, VPN, SHARING, SUPPLICANT, AGENTS, SETTINGS, SUSPEND, CORE, DEVICE, OLPC, WIMAX

```

Anyone can help me tidy the mess I've done? Or at least force Network Manager to produce logs so I'm not so blind?

---

### Post by lampak on 2011-07-13
Problem solved. I've installed packages from the official Ubuntu repository and copied all default config files from a clear Ubuntu installed on a USB stick.

---

