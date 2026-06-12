---
title: "Port Closed On Torrent"
date: 2009-09-03
forum: General Help
---

### Post by twallace on 2009-09-03
Have tried everthing, HELP? Latest version of Ubuntu and Netgear wireless router.

---

### Post by XCan on 2009-09-03
Configure your router, refer to the manual.

---

### Post by lovinglinux on 2009-09-03
Not enough information to troubleshoot but, opening a port for torrent client is very simple.

Check [portforward.com](http://portforward.com/) for instructions tailored to your router. Make sure you forward to the correct internal IP of your machine. You might need to setup a static IP instead of using DHCP, through the Network manager. If you have more than one computer on your LAN, DHCP will assign the first IP available to the first connected machine, so your internal IP might change eventually and require new forwarding settings.

Check if you have any firewall rules blocking your torrent port.

Check if the torrent client is configured t use the same port forwarded by your router. I recommend any port between 49152 and 65535.

That's all you need.

I wouldn't trust some clients reports about closed ports. Some of them rely on pinging a server that might be down or unreachable. To check if the port is opened, visit [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) and scan the port while running the torrent client. The report should say "Open" port. 

To test if everything is running fine, download an [Ubuntu torrent](http://www.ubuntu.com/getubuntu/downloadmirrors#bt). This way you will test a torrent that uses a reliable tracker, usually with many seeders.

---

### Post by twallace on 2009-09-03
Haven't tried the static IP thing yet, will give that a try tonight after work. Looks like everything is ok when I change the settings in my router but when I look at the Torrent program it says port closed. Also note the ISO I am trying to download; Linux Mint, shows no connected peers and just stays idle.

---

### Post by lovinglinux on 2009-09-03
> **twallace said:**
> Haven't tried the static IP thing yet, will give that a try tonight after work. Looks like everything is ok when I change the settings in my router but when I look at the Torrent program it says port closed. Also note the ISO I am trying to download; Linux Mint, shows no connected peers and just stays idle.

You don't need a port open to download. So if you can't connect to any peers, then most likely to be a tracker problem. Check [http://ubuntuforums.org/showpost.php?p=7891181&postcount=3](http://ubuntuforums.org/showpost.php?p=7891181&postcount=3)

---

### Post by aeiah on 2009-09-03
easiest thing to do is probably to enable UPnP on the router and let the torrent program open the ports its self.

---

### Post by twallace on 2009-09-04
Funny thing, tried download from another site and it worked fine without using the torrent program. Now I have to figure out why my CDROM won't burn the ISO...

---

