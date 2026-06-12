---
title: "shutting down network manager and wpa_supplicant etc"
date: 2011-12-04
forum: General Help
---

### Post by jaylc005 on 2011-12-04
Hi guys, how do I shut down all of the services using my network card, without actually removing them?

I have tried to sudo killall the processes I want closed, but they simply restart. Of course, this is ubuntu protecting the newb, and I am a newb in that I dont know how to beat that newb protection. Here is the output..

```

PID    Name
946    NetworkManager
951    avahi-daemon
956    avahi-daemon
1082    wpa_supplicant
1652    dhclient
Process with PID 1652 (dhclient) is running on interface wlan0

```I understand that if I uninstall networkmanager, I need to set up dhcp etc, while this is not an issue, I do not want this type of system, I like the ease of the network manager now and am happy to have this over issuing commands and stuff, but regardless, I need it closed at times where I want to use airodump-ng. I still need to close the other processes.. Maybe a root terminal?

I can kill dhclient for the longest, but its about 5 seconds lol, NetworkManager restarts it, or one of the other processes.

The reason is the problem of having a fixed channel on mon0 to -1, this creates a problem for me in many ways, firstly, the method of solving this works while network manager is in use, from my own testing I can say that, but it is far from ideal, it changes and patches the system in such a way that with 10.10 I kept getting crashes, now I have updated to 11.04 and I have the -1 problem again, suggesting to me that the original patch has been overwritten, I am happy with this now as it means having a stable, up to date system, but I still need to do what I need to do.

Therefore, the best method I can assume is to close anything locking the wificard in managed mode to a certain channel, it is not channel -1 being locked, that is merely the output suggesting that channel cannot be changed to the one specified... At least that is my understanding..

Any ideas ladies and gents? All I want is to achieve is to issue some commands to kill off all control of the network card in managed mode, so that I can control the channel in monitor mode.

Kindest regards.
Jay.

---

