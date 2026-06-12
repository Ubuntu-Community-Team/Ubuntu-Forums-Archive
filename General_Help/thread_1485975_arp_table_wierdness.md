---
title: "arp table wierdness"
date: 2010-05-17
forum: General Help
---

### Post by tmurch on 2010-05-17
So I was wondering if someone could inform me what the total time before and arp entry is removed from the arp table as it appears to be set to 5 minutes in 9.10 ubuntu
Is there some place I can set the arp table to 30 minutes before a deletion takes place?

Thanks 

Tom 

 tmurch@:~$ date
Mon May 17 11:46:09 EDT 2010

tmurch@:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
ntps22i.lan.us       ether   00:04:76:e4:98:5a   C                     eth0
u8-eth1.lan.us       ether   00:06:28:cf:ee:60   C                     eth0
u3-eth0.lan          ether   00:50:54:a5:a4:e0   C                     eth0
meinberg.lan.us      ether   00:13:95:00:76:ee   C                     eth0
gw-psn.lan.us        ether   00:00:5e:00:01:dc   C                     eth0
u22-eth0.lan.us      ether   00:04:dd:bb:e9:41   C                     eth0
u18-eth1.lan.us      ether   00:04:4d:56:7d:41   C                     eth0
u30-eth2.lan         ether   00:1d:e5:35:c7:c1   C                     eth0
ds200.lan.us         ether   00:00:24:c5:f4:70   C                     eth0

tmurch@:~$ date
Mon May 17 11:46:29 EDT 2010

tmurch@:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
ntps22i.lan.us       ether   00:04:76:e4:98:5a   C                     eth0
u3-eth0.lan          ether   00:50:54:a5:a4:e0   C                     eth0
meinberg.lan.us      ether   00:13:95:00:76:ee   C                     eth0
gw-psn.lan.us        ether   00:00:5e:00:01:dc   C                     eth0
u22-eth0.lan.us      ether   00:04:dd:bb:e9:41   C                     eth0
u18-eth1.lan.us      ether   00:04:4d:56:7d:41   C                     eth0

tmurch@:~$ uname -a
Linux  2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

tmurch@:~$ date
Mon May 17 11:48:13 EDT 2010

tmurch@:~$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
ntps22i.lan.us       ether   00:04:76:e4:98:5a   C                     eth0
u3-eth0.lan          ether   00:50:54:a5:a4:e0   C                     eth0
meinberg.lan.us      ether   00:13:95:00:76:ee   C                     eth0
gw-psn.lan.us        ether   00:00:5e:00:01:dc   C                     eth0
u22-eth0.lan.us      ether   00:04:dd:bb:e9:41   C                     eth0
ds200.lan.us         ether   00:00:24:c5:f4:70   C                     eth0

---

### Post by gmargo on 2010-05-17
The arp protocol can be tuned by writing to a file(s) in the /proc filesystem.

**/proc/sys/net/<protocol>/neigh/<dev>/***

I think you can get what you want by increasing the **gc_stale_time** value.
Google for "gc_stale_time" for more info.

---

