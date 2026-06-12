---
title: "Internet Security"
date: 2006-05-18
forum: General Help
---

### Post by Geffers on 2006-05-18
My small home network operates behind a NAT router that also has a few IP rules set.

My Windows machines also have a software firewall installed (ZoneAlarm) as well as a Virus Checker (AVG).

At the moment I have neither installed on my Ubuntu system, any suggestions as to what would be advisable.

Geffers

---

### Post by xXx 0wn3d xXx on 2006-05-18
[QUOTE=Geffers]My small home network operates behind a NAT router that also has a few IP rules set.

My Windows machines also have a software firewall installed (ZoneAlarm) as well as a Virus Checker (AVG).

At the moment I have neither installed on my Ubuntu system, any suggestions as to what would be advisable.

Geffers[/QUOTE]
Hello, Ubuntu is already fairly secure. Ubuntu has a built-in firewall called iptables and it works great. There are also almost no viruses or spyware for Ubuntu and to reduce the risk, don't always run as root. Use sudo. 

I would recommend that you use firestarter. It is not a firewall but a GUI to set rules for the firewall.

> sudo apt-get install firestarter

Follow [ this guide ](http://ubuntuforums.org/showthread.php?t=110320&highlight=firestarter+start+boot) to make it load at boot.

Since you are running a network with windows, you may want to install anti-virus so you don't pass a viruses from Ubuntu to Windows (Ubuntu will not be infected, but it may spread to windows) follow [ this tutorial ](http://ubuntuforums.org/showthread.php?t=136064&highlight=avg) to install AVG anti-virus. You don't need to run it all the time, just once every few days. (3-7)

---

