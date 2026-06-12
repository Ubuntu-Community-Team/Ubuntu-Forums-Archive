---
title: "Torrents Not downloading"
date: 2011-03-01
forum: General Help
---

### Post by BeastModeJoshFreeman#5 on 2011-03-01
alright i have been using ubuntu for a  few months now and ive never had any issues downloading torrents until now. Whenever i open transmission and i download a torrent from Vodo it never downloads. Its stays at zero the whole time. It does not look for peers or any of that stuff. i tried to change ports but it says all of them are closed in transmission. I tried using opera's ittorrent integration to download but that wouldnt help either.....PLEASE HELP!

---

### Post by LOIREE on 2011-03-01
> **BeastModeJoshFreeman#5 said:**
> alright i have been using ubuntu for a  few months now and ive never had any issues downloading torrents until now. Whenever i open transmission and i download a torrent from Vodo it never downloads. Its stays at zero the whole time. It does not look for peers or any of that stuff. i tried to change ports but it says all of them are closed in transmission. I tried using opera's ittorrent integration to download but that wouldnt help either.....PLEASE HELP!

Hey!

Could you please insure that:
a) these ports are opened on your router (if you have one) or UPNP is enabled
b) your ISP is not blocking torrent traffic, or these ports
c) you have firewall software installed that is blocking these ports?

---

### Post by seawolf167 on 2011-03-01
> **BeastModeJoshFreeman#5 said:**
> i tried to change ports but it says all of them are closed in transmission

Echoing some of what loiree said, check:

[LIST=1]
[*]You routers port forwarding rules, ensure the correct port [ranges] are forwarded to your machine
[*]Ensure any firewalls you have active have rules to allow the application ports through (I suggest switching to gufw if you are currently using firestarter)
[*]Ensure if you are on a private tracker that you have permission to use it to receive peers (valid torrent file & account info)
[*]Check that your ISP isn't blocking said ptp traffic
[/LIST]

---

### Post by BeastModeJoshFreeman#5 on 2011-03-01
i do not have a router. i have a dsl moddem.......i dont know how to do the rest.....how do i unblock ports.......i dont think i have a firewall

---

### Post by seawolf167 on 2011-03-01
> **BeastModeJoshFreeman#5 said:**
> i do not have a router. i have a dsl moddem

Same thing, run this command, find the line that says "default", then read the second column (its the "Gateway" column).

```
route
```Use this default gateway, and in Firefox, type the address in the address bar with an "http://" in front of it. You'll have something that looks like this:

```
http://192.168.0.1/
```Where the 192.168.0.1 is your default gateway.

From here, you can forward ports in your modem to your computer. You'll want to forward the port that you have open in your torrent client. 

To find the IP address of your machine to forward the port to, type the command

```
ipconfig
```Your IP address is listed (prob under eth0) as "inet addr: xxx.xxx.xxx.xxx"

Ubuntu's firewall is disabled by default so no worries there unless you install and activate one

---

### Post by BeastModeJoshFreeman#5 on 2011-03-02
still not working

---

### Post by DarthScape on 2011-03-02
Try downloading with Deluge. That will at least tell you if it is a Network or an Application issue.

---

