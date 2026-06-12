---
title: "System slow-down"
date: 2009-11-29
forum: General Help
---

### Post by rlntel on 2009-11-29
Hello All,

My Sony VGN-FE670G laptop is running very slow, especially Firefox.

After loading Karmic, I get a 'Hard Drive has many bad sectors' warning. I'm inclined to replace the HD, but it worked fine before moving to Karmic so I wanted to ask if the slowdown may be caused by other problems.

An archived post suggested to run 'top' and post the results. Here are mine:

top - 12:06:47 up 4 days, 15:44,  2 users,  load average: 0.48, 0.47, 0.50
Tasks: 188 total,   1 running, 187 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.2%us,  5.2%sy,  0.0%ni, 80.4%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   2052236k total,  1815736k used,   236500k free,    58620k buffers
Swap:  4016208k total,   136616k used,  3879592k free,   350244k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                      
 3029 letterre  20   0 1469m 992m  33m S   18 49.5   1022:33 firefox                                                                                      
 1320 root      20   0  103m  29m  12m S   11  1.5  31:31.79 Xorg                                                                                         
22313 letterre  20   0 38352  13m 9768 S    7  0.7   0:05.22 gnome-terminal                                                                               
 1927 letterre  20   0  156m 4380 3452 S    1  0.2  12:50.01 pulseaudio                                                                                   
 6382 letterre  20   0  122m  47m  16m S    1  2.4   2:46.16 pidgin                                                                                       
 1986 letterre  20   0 43704  16m  11m S    1  0.8   1:31.21 gnome-panel                                                                                  
 1492 root      20   0  8988 1236  976 S    0  0.1   0:02.35 nmbd                                                                                         
 2362 letterre  20   0  237m  96m  21m S    0  4.8  10:27.21 thunderbird-bin                                                                              
 2709 letterre  20   0  384m 123m  41m S    0  6.1   6:51.01 soffice.bin                                                                                  
 2758 letterre  20   0 64312  18m  11m S    0  0.9   0:12.11 tomboy                                                                                       
22418 letterre  20   0  2468 1212  884 R    0  0.1   0:00.25 top                                                                                          
    1 root      20   0  2628 1412 1084 S    0  0.1   0:01.14 init                                                                                         
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                     
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                  
    4 root      15  -5     0    0    0 S    0  0.0   0:17.50 ksoftirqd/0                                                                                  
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                   
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                  
    7 root      15  -5     0    0    0 S    0  0.0   0:01.48 ksoftirqd/1                                                                                  
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                   
    9 root      15  -5     0    0    0 S    0  0.0   0:00.29 events/0                                                                                     
   10 root      15  -5     0    0    0 S    0  0.0   0:00.14 events/1                                                                                     
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                       
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                      
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns                                                                                        
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                    
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                
   17 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0     

______________________________________________________________________

These number mean very little to me.

The next suggestion was to run 'dig' to see if a lame DNS entry was the cause. Here's its output:

; <<>> DiG 9.6.1-P1 <<>>
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63586
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 14

;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			404532	IN	NS	M.ROOT-SERVERS.NET.
.			404532	IN	NS	C.ROOT-SERVERS.NET.
.			404532	IN	NS	J.ROOT-SERVERS.NET.
.			404532	IN	NS	I.ROOT-SERVERS.NET.
.			404532	IN	NS	E.ROOT-SERVERS.NET.
.			404532	IN	NS	K.ROOT-SERVERS.NET.
.			404532	IN	NS	F.ROOT-SERVERS.NET.
.			404532	IN	NS	A.ROOT-SERVERS.NET.
.			404532	IN	NS	D.ROOT-SERVERS.NET.
.			404532	IN	NS	L.ROOT-SERVERS.NET.
.			404532	IN	NS	H.ROOT-SERVERS.NET.
.			404532	IN	NS	B.ROOT-SERVERS.NET.
.			404532	IN	NS	G.ROOT-SERVERS.NET.

;; ADDITIONAL SECTION:
C.ROOT-SERVERS.NET.	105838	IN	A	192.33.4.12
J.ROOT-SERVERS.NET.	59010	IN	A	192.58.128.30
J.ROOT-SERVERS.NET.	511113	IN	AAAA	2001:503:c27::2:30
I.ROOT-SERVERS.NET.	58986	IN	A	192.36.148.17
E.ROOT-SERVERS.NET.	492023	IN	A	192.203.230.10
K.ROOT-SERVERS.NET.	491870	IN	A	193.0.14.129
K.ROOT-SERVERS.NET.	492748	IN	AAAA	2001:7fd::1
F.ROOT-SERVERS.NET.	562192	IN	A	192.5.5.241
F.ROOT-SERVERS.NET.	592047	IN	AAAA	2001:500:2f::f
A.ROOT-SERVERS.NET.	58917	IN	A	198.41.0.4
A.ROOT-SERVERS.NET.	493481	IN	AAAA	2001:503:ba3e::2:30
D.ROOT-SERVERS.NET.	59010	IN	A	128.8.10.90
L.ROOT-SERVERS.NET.	58917	IN	A	199.7.83.42
L.ROOT-SERVERS.NET.	491575	IN	AAAA	2001:500:3::42

;; Query time: 222 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Nov 29 12:08:05 2009
;; MSG SIZE  rcvd: 512

_____________________________________________________________________


If replacing the HD is the best option, what is the best way to run the install? Burn a new Karmic cd before unloading the existing HD, then install the new HD and run the install; finally, copying data from the old HD to the new?

All help is welcome.

Thanks, Rob

---

### Post by rlntel on 2009-11-29
Solved - I figured it out...ran about:config from the FF address bar and changed network.dns.disableIPv6 to True...works great now!

Thanks anyway!

---

