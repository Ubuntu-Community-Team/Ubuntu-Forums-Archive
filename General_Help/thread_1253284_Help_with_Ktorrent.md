---
title: "Help with Ktorrent"
date: 2009-08-29
forum: General Help
---

### Post by Rick Abraham on 2009-08-29
Hi I use to use uTorrent in Windows and my download speeds averaged around 160kbps, 
I have now done the shift to Ubuntu and I am using Ktorrent but my download speeds are very poor I havent seen anything above 10kbps.

Does anyone know why this is ??

I have opened the port in Ubuntu using this command

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

but it didnt change anything.
Im still using the same router, IP provider etc so I carnt work  it out.
Any help would be great.

---

### Post by lovinglinux on 2009-08-30
- Check if the port is forwarded from the router to the correct internal IP of your machine.
- Check if the port opened in the firewall is the same as the one opened in the router and the one used by the torrent client. I do not recommend using ports between 6881-6889, because some ISP cap the bandwidth on those ports or completely block them. I recommend using any port between 49152 to 65535.

To check if a port is really opened and properly forwarded, start your torrent client and scan the port with [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)

you should get an "Open" status in the results.

BTW, I personally recommend Deluge.

---

