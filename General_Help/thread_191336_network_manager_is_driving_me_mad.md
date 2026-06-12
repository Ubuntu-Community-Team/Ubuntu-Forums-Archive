---
title: "network manager is driving me mad"
date: 2006-06-07
forum: General Help
---

### Post by sonicyoof on 2006-06-07
Hi all,

I just got a Thinkpad X31 - I swiftly binned the windows installation and installed Ubuntu 6.06

I'm trying to get network manager working. It's installed and running, yet I don't get the applet on the gnome panel. Here's what I've done to try and correct this:

1. updated to latest version of network manager: 0.6.2-0ubuntu7
2. sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/    (found this suggestion on google)
3. checked that nm-applet is running on startup - it already was (nm-applet --sm-disable)
4. tried starting it again from terminal - nm-applet &  
5. commented out all interfaces apart from lo in /etc/network/interfaces
6. sudo killall NetworkManager
7. sudo /etc/init.d/networking restart


still no applet anywhere :(

any ideas?

thanks..

---

### Post by hegenious on 2006-06-07
what I did to get it working...

karim@ubuhome:/usr/share/omf/vnc$ sudo apt-get install nm-applet
Password:
Reading package lists... Done
Building dependency tree... Done
Note, selecting network-manager-gnome instead of nm-applet
The following extra packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome
The following NEW packages will be installed:
  dhcdbd libnl1-pre6 libnm-util0 network-manager network-manager-gnome
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 704kB of archives.
After unpacking 2748kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main dhcdbd 1.10-0ubuntu11 [42.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libnl1-pre6 1.0~pre5+svn21-2ubuntu2 [76.5kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libnm-util0 0.6.2-0ubuntu7 [116kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main network-manager 0.6.2-0ubuntu7 [228kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main network-manager-gnome 0.6.2-0ubuntu7 [241kB]
Fetched 704kB in 0s (1839kB/s)
Selecting previously deselected package dhcdbd.
(Reading database ... 105822 files and directories currently installed.)
Unpacking dhcdbd (from .../dhcdbd_1.10-0ubuntu11_i386.deb) ...
Selecting previously deselected package libnl1-pre6.
Unpacking libnl1-pre6 (from .../libnl1-pre6_1.0~pre5+svn21-2ubuntu2_i386.deb) ...
Selecting previously deselected package libnm-util0.
Unpacking libnm-util0 (from .../libnm-util0_0.6.2-0ubuntu7_i386.deb) ...
Selecting previously deselected package network-manager.
Unpacking network-manager (from .../network-manager_0.6.2-0ubuntu7_i386.deb) ...
Selecting previously deselected package network-manager-gnome.
Unpacking network-manager-gnome (from .../network-manager-gnome_0.6.2-0ubuntu7_i386.deb) ...
Setting up dhcdbd (1.10-0ubuntu11) ...
 * Reloading system message bus config                                                                                                                                       [ ok ]
 * Stopping DHCP client manager...                                                                                                                                           [fail]
 * Starting DHCP client manager...                                                                                                                                           [ ok ]

Setting up libnl1-pre6 (1.0~pre5+svn21-2ubuntu2) ...

Setting up libnm-util0 (0.6.2-0ubuntu7) ...
Setting up network-manager (0.6.2-0ubuntu7) ...
 * Reloading system message bus config                                                                                                                                       [ ok ]
 * Stopping NetworkManager daemon                                                                                                                                            [ ok ]
 * Starting NetworkManager daemon                                                                                                                                            [ ok ]
 * Stopping NetworkManager dispatcher                                                                                                                                        [ ok ]
 * Starting NetworkManager dispatcher                                                                                                                                        [ ok ]

Setting up network-manager-gnome (0.6.2-0ubuntu7) ...

karim@ubuhome:/usr/share/omf/vnc$  nm-applet

and there it is sitting in the notification area

---

### Post by sonicyoof on 2006-06-07
hmm.. that worked straight off on my desktop, but not on my laptop..

---

