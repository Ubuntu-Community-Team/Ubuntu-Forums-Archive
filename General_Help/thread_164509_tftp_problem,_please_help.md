---
title: "tftp problem, please help"
date: 2006-04-22
forum: General Help
---

### Post by lezz on 2006-04-22
hi

i just installed a tftp daemon with apt-get install tftpd-hpa. but when i cant connect to /tftpboot from my other laptop.

/etc/inetd.conf:

tftp		dgram	udp	wait 	nobody /usr/sbin/tcpd /usr/sbin/in.tftpd --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  /tftpboot

netstat --listening-ports --numeric-port:

Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:901             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:538             0.0.0.0:*               LISTEN
udp        0      0 0.0.0.0:538             0.0.0.0:*
udp        0      0 0.0.0.0:67              0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 192.168.0.1:123         0.0.0.0:*
udp        0      0 213.67.187.165:123      0.0.0.0:*
udp        0      0 192.168.1.2:123         0.0.0.0:*
udp        0      0 192.168.1.1:123         0.0.0.0:*
udp        0      0 127.0.0.1:123           0.0.0.0:*
udp        0      0 0.0.0.0:123             0.0.0.0:*
udp6       0      0 :::123                  :::*
raw        0      0 0.0.0.0:1               0.0.0.0:*               7

what is wrong?

i have also tested all the other tftpd daemons but none of them worked. im not behind a firewall and ive got a verified connection between my computers.

---

