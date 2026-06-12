---
title: "Devices&amp;Network"
date: 2009-09-22
forum: General Help
---

### Post by eaglemob on 2009-09-22
[B]I need help how to configure my network devices so they can work uploading torrents.
My configuration: provider is a DHCP DSL Dynamic ip, so the ip can change.
I have 2 network cards on the motherboard, just one i have connected ETH0.

How do i configure the:
Loop back (lo), ETHO, ipv4,Ipv6 ?

On /etc/network/interfaces i have this:
[/B]
auto lo
iface lo inet loopback

**Tested with the torrent client runing**
netstat -anp --tcp --udp | grep LISTEN
tcp         0      0 0.0.0.0:55555           0.0.0.0:*            LISTEN      4409/transmission
tcp         0      0 0.0.0.0:10000           0.0.0.0:*            LISTEN      -               
tcp         0      0 127.0.0.1:631           0.0.0.0:*            LISTEN      -               
tcp6       0      0 :::55555                     :::*                    LISTEN      4409/transmission
tcp6       0      0 ::1:631                       :::*                    LISTEN      -

Downloading torrents is no problem, it works perfect.
Allso downloading and uploading from and to a ftp allso no problem.
I have no clue how to make this work with uploading(seed) torrents.
Any of you could give me hand on this please ?

Thx.

---

