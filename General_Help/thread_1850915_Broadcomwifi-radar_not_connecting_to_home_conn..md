---
title: "Broadcom/wifi-radar not connecting to home conn."
date: 2011-09-27
forum: General Help
---

### Post by dann_radkov on 2011-09-27
Hello ppl,
I installed Slackware 13.37 on Acer Extensa 4420 notebook.
So far it works ok.Straight to the question.I installed the drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .
I followed the instructions down to the last detail.
a)untarred the file
tar xzf <path>/hybrid-portsrc_x86-32_v5.100.82.38.tar.gz
b)navigated to directory and did a make command
c)build produced a wl.ko file
d)did a modprobe lib80211 
e)did a insmod wl.ko
f)wifi radar and my wifi radar(that i have already installed but didnt configure anything, started)
g)now when I start wifi radar it asks me for a profile

I removed all wifi security in terms of passwords etc on the router to avoid any trouble.
I added the MAC address to the router so it can recognize the Linux slackware laptop.
Wifi radar starts ok but I get a "Could not get an IP address" after 2 secs.
In the background the Slackware terminal shows:

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.
/sbin/dhcpcd: invalid option -- 'D'
usage: dhcpcd [-adknpEGHMNRSTY] [-c script] [-h hostname] [-i classID]
              [-l leasetime] [-m metric] [-r ipaddress] [-s ipaddress]
              [-t timeout] [-u userclass] [-F none | ptr | both]
              [-I clientID] <interface>

Can you let me know what else should I configure to get my wifi up and running on this laptop.
Thanks.

---

### Post by andrew.46 on 2011-09-27
Hmmm.... do you need firmware for your broadcom as well? Have a look at slackbuilds.org for a neater installation of STA driver / firmware etc and [here]("http://www.linuxquestions.org/questions/slackware-14/") for better Slackware support.

My own broadcom 4312 runs nicely under 13.37 with b43 fwcutter, firmware 4.174.64.19 and wicd from /extra (which I would highly recommend). You will find many threads on Linux Questions to do with broadcom chips...

---

### Post by dann_radkov on 2011-09-28
I installed wicd easily. Everybody should check the following [http://ubuntuforums.org/showthread.php?t=1524810](http://ubuntuforums.org/showthread.php?t=1524810)

Please mark thread as solved

---

### Post by andrew.46 on 2011-09-28
Good to hear all is resolved :). You can mark the thread as 'Solved' by going to the 'Thread Tools' dropdown box at the top of the thread.

---

