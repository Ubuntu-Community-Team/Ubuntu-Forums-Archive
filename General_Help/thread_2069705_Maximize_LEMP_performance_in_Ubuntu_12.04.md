---
title: "Maximize LEMP performance in Ubuntu 12.04"
date: 2012-10-11
forum: General Help
---

### Post by hunterlove22 on 2012-10-11
Hello 

I am using EC2 instance in Amazon, My site has a huge traffic, about 30k-40k concurrent connections, I installed a mysql server and others for web service with load balancing, but my web server using nginx + php-fastcgi doesnt work well. I cant bear for 10 mins. All died.

Please share your experience huge traffic configuration in ubuntu. 



Here is some info

> root@x:/etc/nginx# cat /proc/cpuinfo | grep process
processor       : 0
processor       : 1
processor       : 2
processor       : 3

> root@x:/etc/nginx# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 44
model name      : Intel(R) Xeon(R) CPU           E5645  @ 2.40GHz
stepping        : 2
microcode       : 0x13
cpu MHz         : 2000.070
cache size      : 12288 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 32
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu de tsc msr pae cx8 sep cmov pat clflush mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good nopl nonstop_tsc pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 popcnt aes hypervisor lahf_lm
bogomips        : 4000.14
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

Memory:

> root@x:/etc/nginx# cat /proc/meminfo
MemTotal:       15339676 kB
MemFree:        13649292 kB
Buffers:           76856 kB
Cached:          1148320 kB
SwapCached:            0 kB
Active:           719880 kB
Inactive:         721532 kB
Active(anon):     216368 kB
Inactive(anon):     4276 kB
Active(file):     503512 kB
Inactive(file):   717256 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                12 kB
Writeback:             0 kB
AnonPages:        216288 kB
Mapped:            18504 kB
Shmem:              4404 kB
Slab:              69820 kB
SReclaimable:      56108 kB
SUnreclaim:        13712 kB
KernelStack:        1040 kB
PageTables:         7488 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7669836 kB
Committed_AS:     680416 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       40780 kB
VmallocChunk:   34359695440 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:    15736832 kB
DirectMap2M:           0 kB


Some of my sysctl.conf

> net.ipv4.ip_local_port_range = 2000 65000


net.ipv4.tcp_window_scaling = 1


# number of packets to keep in backlog before the kernel starts dropping them
net.ipv4.tcp_max_syn_backlog = 3240000


# increase socket listen backlog
net.core.somaxconn = 3240000
net.ipv4.tcp_max_tw_buckets = 1440000

# Increase TCP buffer sizes
net.core.rmem_default = 8388608
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
net.ipv4.tcp_congestion_control = cubic
fs.file-max=5049800
net.unix.max_dgram_qlen = 3240000

php-fastcgi startup

> #!/bin/bash
BIND=/tmp/php.socket
USER=www-data
PHP_FCGI_CHILDREN=30
PHP_FCGI_MAX_REQUESTS=30000

PHP_CGI=/usr/bin/php-cgi

Here is some kind of error from nginx

```
2012/10/11 07:57:41 [error] 1372#0: *649643 connect() to unix:/tmp/php.socket failed (111: Connection refused) while connecting to upstream, client: xxx.xxx.xxx.xxx, server: domain.com, request: "GET / HTTP/1.1", upstream: "fastcgi://unix:/tmp/php.socket:", host: "xxx.xxx.xxx.xxx:80"

```


```
2012/10/11 00:00:13 [error] 1372#0: *877493 connect() to unix:/tmp/php.socket failed (11: Resource temporarily unavailable) while connecting to upstream, client: xxx.xxx.xxx.xxx, server: domain.com, request: "GET /xml.php HTTP/1.1", upstream: "fastcgi://unix:/tmp/php.socket:", host: "domain.com"

```


This is very urgent for me. Please help because server is down.

Thanks,

---

