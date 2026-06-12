---
title: "cannot sync time"
date: 2009-10-17
forum: General Help
---

### Post by ikki_72 on 2009-10-17
```
umarzuki@umarzuki-desktop:~$ sudo /usr/sbin/ntpdate pool.ntp.org
17 Oct 20:14:27 ntpdate[16002]: sendto(ns1.epiweb.com.my): Operation not permitted
17 Oct 20:14:27 ntpdate[16002]: sendto(121.122.129.99): Operation not permitted
17 Oct 20:14:28 ntpdate[16002]: sendto(ns1.epiweb.com.my): Operation not permitted
17 Oct 20:14:28 ntpdate[16002]: sendto(121.122.129.99): Operation not permitted
17 Oct 20:14:29 ntpdate[16002]: sendto(ns2.epiweb.com.my): Operation not permitted
17 Oct 20:14:34 ntpdate[16002]: sendto(121.122.129.99): Operation not permitted
17 Oct 20:14:35 ntpdate[16002]: sendto(ns1.epiweb.com.my): Operation not permitted
17 Oct 20:14:35 ntpdate[16002]: sendto(121.122.129.99): Operation not permitted
17 Oct 20:14:36 ntpdate[16002]: no server suitable for synchronization found
```


```
umarzuki@umarzuki-desktop:~$ tail /var/log/messages
Oct 17 20:07:32 umarzuki-desktop kernel: [ 2409.586688] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=213.173.244.123 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=35067 DF PROTO=TCP SPT=50091 DPT=18963 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:32 umarzuki-desktop kernel: [ 2409.586802] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=213.173.244.123 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=41326 DF PROTO=TCP SPT=50094 DPT=18963 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:33 umarzuki-desktop kernel: [ 2410.582437] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=157.157.73.123 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=44273 DF PROTO=TCP SPT=56831 DPT=51413 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:33 umarzuki-desktop kernel: [ 2410.594655] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=186.28.13.127 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=16502 DF PROTO=TCP SPT=60649 DPT=52001 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:34 umarzuki-desktop kernel: [ 2411.590183] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=76.171.144.125 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=56797 DF PROTO=TCP SPT=46672 DPT=11965 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:34 umarzuki-desktop kernel: [ 2411.590301] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=76.171.144.125 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=64917 DF PROTO=TCP SPT=46675 DPT=11965 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:35 umarzuki-desktop kernel: [ 2412.585934] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=213.173.244.123 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=41327 DF PROTO=TCP SPT=50094 DPT=18963 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:35 umarzuki-desktop kernel: [ 2412.598155] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=68.13.181.127 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=10518 DF PROTO=TCP SPT=50113 DPT=8805 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:36 umarzuki-desktop kernel: [ 2413.593681] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=186.28.13.127 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=16503 DF PROTO=TCP SPT=60649 DPT=52001 WINDOW=5808 RES=0x00 SYN URGP=0 
Oct 17 20:07:36 umarzuki-desktop kernel: [ 2413.593811] Outbound IN= OUT=eth0 SRC=192.168.0.2 DST=186.28.13.127 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=9221 DF PROTO=TCP SPT=60652 DPT=52001 WINDOW=5808 RES=0x00 SYN URGP=0
``` 

how do i solve this?

---

