---
title: "Load Balancing not working"
date: 2011-03-21
forum: General Help
---

### Post by paulmchugh on 2011-03-21
Hi Everyone, I hope someone can help me out here.....

I've got two physical servers, each running two lucid server VMs (vboxheadless), one LAMP server and the other a Load Balancer:

Physical Server 1[INDENT]LAMP1: 192.168.9.111
LB1:     192.168.9.121

[/INDENT]Physical Server 2[INDENT]LAMP2: 192.168.9.112
LB2:     192.168.9.122
[/INDENT]The LBs are running heartbeat, ipvsadm and ldirectord installed by following the tutorial at:
[http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04-p4](http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04-p4)

My config files look like this:

/etc/ha.d/ha.cf 
```
logfacility local0
ucast eth0 192.168.9.121 # Linux
mcast eth0 225.0.0.1 694 1 0
auto_failback off
node lb1.mydomain.local
node lb2.mydomain.local
respawn hacluster /usr/lib/heartbeat/ipfail
apiauth ipfail gid=haclient uid=hacluster
```
/etc/ha.d/haresources
```
lb1.mydomain.local \
        ldirectord::ldirectord.cf \
        LVSSyncDaemonSwap::master \
        IPaddr2::192.168.9.130/8/eth0/192.168.9.255
```/etc/ha.d/ldirectord.cf
```
checktimeout=10
checkinterval=2
autoreload=no
logfile="local0"
quiescent=yes

virtual=192.168.9.130:80
        real=192.168.9.111:80 gate
        real=192.168.9.112:80 gate
        fallback=127.0.0.1:80 gate
        service=http
        request="/loadb/loadb.html"
        receive="Test Page"
        scheduler=rr
        protocol=tcp
        checktype=negotiate
```I've also got /etc/ha.d/authkeys setup the same on both servers.

The problem is that heartbeat does not appear to be starting ldirectord at startup, and even when I start the service manually on both servers I can't ping or get any web output from the virtual IP address. Running ldirectord in debug mode (-d) shows that it is talking to the LAMP servers OK and finding the test page but nothing is coming back to the client. I've been at this for 3 days now and just about ready to start pulling my hair out!

Many thanks,

Paul

---

