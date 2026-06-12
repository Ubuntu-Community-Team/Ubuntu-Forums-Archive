---
title: "Loopback not working on boot"
date: 2006-04-27
forum: General Help
---

### Post by Blutack on 2006-04-27
Hello there, running Breezy. Since installation cups has been messed up. Sorted out all the permissions stuff and now works great - but the loopback does not. After a fresh boot typing ```
 sudo ifconfig lo 
``` Shows that the interface exists but does not show an inet address or subnet. I have to type ```
 sudo ifconfig lo 127.0.0.1 
``` after which cups is hunky dory. I tried adding the following script both to init.rc (with defaults) and then when that failed to the .kde Autostart folder with no result. ```
 #! /bin/sh - # $Id$ sudo ifconfig lo 127.0.0.1 exit 
``` Having never written a bash script I modelled it on one of the init.rc scripts. It works when I run it from a terminal after boot, but not at the time of. Also I get the following message when I type ```
 blutack@icebox:~$ sudo ifdown -a /etc/network/interfaces:19: too few parameters for iface line ifdown: couldn't read interfaces file "/etc/network/interfaces" 
``` However this could be because at present I am using my ndiswrapped wlan card, which I configure with iwconfig each time I use it (rarely) Here is my interfaces file >  # This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5). # The loopback network interface auto lo iface lo inet loopback address 127.0.0.1 netmask 255.0.0.0 # This is a list of hotpluggable network interfaces. # They will be activated automatically by the hotplug subsystem. mapping hotplug script grep map eth0 iface wlan0 inet dhcp wireless-essid WLAN iface eth0 inet  I have not edited this manually (although I did fiddle with Network Connections when I was more of a nube). Anything fundamental I am missing? Please help. Or any other duct-tape type approaches. I am sick of rebooting OO everytime I forget to ifconfig before printing. Many thanks guys and girls! :confused:

---

### Post by GeneralZod on 2006-04-27
Try commenting out the final ("iface eth0 inet") line - it is incomplete, and is causing /etc/network/interfaces to be improperly parsed.

Also, just in case you were curious, the "KDE Autostart" thing didn't work because "sudo" requires the user to type in their password, which they obviously can't do in this case since the script is not started by the user :) Using kdesu instead of sudo may have worked, though.

---

### Post by Blutack on 2006-04-29
General you are a prince amongst men.  Many thanks.  (Just imagining with the glee the registry hacks I woulda needing if that was XP...)

---

