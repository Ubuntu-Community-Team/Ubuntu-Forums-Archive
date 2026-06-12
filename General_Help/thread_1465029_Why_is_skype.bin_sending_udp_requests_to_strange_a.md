---
title: "Why is skype.bin sending udp requests to strange addresses?"
date: 2010-04-29
forum: General Help
---

### Post by mdougher on 2010-04-29
Weird network traffic on skype 1.0.3.0.0.93 on Ubuntu 9.10

OK.... snort finds what it belives to be a udp port scan and it's being conducted by skype.   THe addresses seem to be user addresses in service provider pools (comcast, fios, etc.).

root@mdougher-laptop:/tmp# netstat -ap |grep 74.105.44.213
root@mdougher-laptop:/tmp# netstat -ap |grep fios
root@mdougher-laptop:/tmp# netstat -ap |grep 11799
tcp        0      0 *:11799                 *:*                     LISTEN      23330/skype.bin 
udp        0      0 *:11799                 *:*                                 23330/skype.bin 

output from tcpdump:

00:56:16.669566 IP mdougher-laptop.local.11799 > pool-74-105-44-213.nwrknj.fios.verizon.net.64517: UDP, length 97
00:56:18.670284 IP mdougher-laptop.local.11799 > pool-74-105-44-213.nwrknj.fios.verizon.net.64517: UDP, length 97
00:56:19.700637 IP pool-74-105-44-213.nwrknj.fios.verizon.net > mdougher-laptop.local: ICMP host pool-74-105-44-213.nwrknj.fios.verizon.net unreachable, length 133
00:56:19.700662 IP pool-74-105-44-213.nwrknj.fios.verizon.net > mdougher-laptop.local: ICMP host pool-74-105-44-213.nwrknj.fios.verizon.net unreachable, length 133
00:56:22.675950 IP mdougher-laptop.local.11799 > pool-74-105-44-213.nwrknj.fios.verizon.net.64517: UDP, length 97
00:56:25.700999 IP pool-74-105-44-213.nwrknj.fios.verizon.net > mdougher-laptop.local: ICMP host pool-74-105-44-213.nwrknj.fios.verizon.net unreachable, length 133
^C
6 packets captured
6 packets received by filter
0 packets dropped by kernel

---

