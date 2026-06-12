---
title: "Configuration Heartbeat with HAProxy"
date: 2011-05-18
forum: General Help
---

### Post by tranen on 2011-05-18
Hi,

I did a configuration heartbeat-apache which is working well.
 Now I try to do it with haproxy but it didn't work.
 I think that maybe it's because I use a different port in haproxy than the default port.
 In haproxy configuration I have this : listen webfarm 192.168.0.99:8080
 In heartbeat configuration :
 logfacility daemon
 keepalive 2
 deadtime 15
 warntime 5
 initdead 120
 udpport 694
 ucast eth1 192.168.0.99 
 auto_failback on
 node master 
 node slave 
 respawn hacluster /usr/lib/heartbeat/ipfail
 use_logd yes

so how it's possible to configure heartbeat on the appropriate port?

Thanks

---

