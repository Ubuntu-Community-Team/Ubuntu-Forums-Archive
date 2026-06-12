---
title: "DNS Works only locally"
date: 2011-01-03
forum: General Help
---

### Post by apnkpp on 2011-01-03
Hi.

I have tried to host a website at home (consider it a good  option and learning experience). After using some Linux distros finally  decided to stick with UBUNTU (10.10). Sadly everything was ok until the  configuration of BIND9 finally failed.

I am nearly blind with  most concepts of networking, my understanding is really basic and am  guessing my problem is on that direction but really can not figure it  out.

My set up is based on a guide found at  [https://help.ubuntu.com/10.10/serverguide/C/dns.html](https://help.ubuntu.com/10.10/serverguide/C/dns.html) and have just  changed the domain name so my configuration files are:

Added the following to /etc/bind/named.conf.local

zone "arquibailleres.com"{
    type master;
    file "/etc/bind/db.arquibailleres.com";
};

zone "9.200.10.in-addr.arpa"{
    type master;
    file "/etc/bind/db.168";
};


Then created the file /etc/bind/db.arquibailleres.com
$TTL    604800
@       IN      SOA     ns.arquibailleres.com. root.arquibailleres.com. (
                             11         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.arquibailleres.com.
@       IN      A       127.0.0.1
@       IN      AAAA    ::1
ns      IN      A       10.200.9.168
www     IN      A       10.200.9.168

And for the reverse zone:

$TTL    604800
@       IN      SOA     ns.arquibailleres.com. root.arquibailleres.com. (
                             11         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
168     IN      PTR     ns.arquibailleres.com.

My resolv.conf file looks as follows:

search arquibailleres.com
nameserver 10.200.9.168
nameserver 200.53.250.1
nameserver 201.130.193.15
nameserver 200.56.200.1

with the last three lines being the IP of my ISP DNSs and declared in /etc/bind/named.conf.options as formwarders.

The output of named-checkzone arquibailleres.com is:

named-checkzone arquibailleres.com /etc/bind/db.arquibailleres.com 
zone arquibailleres.com/IN: loaded serial 11
OK

and:
named-checkzone arquibailleres.com /etc/bind/db.168
zone arquibailleres.com/IN: loaded serial 11
OK

When  my BIND service is restarted its output log clearly states that the  zones are added and indicates "sending notifies" yet by using dig and  ping everything works nicely but when I try to connect to the site from  an external computer my site simply is not recognised.

Ping output:
pingarquibailleres.com
64 bytes from PINFLO-SRVR01 (127.0.0.1): icmp_req=1 ttl=64 time=0.027 ms
64 bytes from PINFLO-SRVR01 (127.0.0.1): icmp_req=2 ttl=64 time=0.033 ms
64 bytes from PINFLO-SRVR01 (127.0.0.1): icmp_req=3 ttl=64 time=0.034 ms
64 bytes from PINFLO-SRVR01 (127.0.0.1): icmp_req=4 ttl=64 time=0.036 ms
64 bytes from PINFLO-SRVR01 (127.0.0.1): icmp_req=5 ttl=64 time=0.031 ms

Dig output:

dig arquibailleres.com

; <<>> DiG 9.7.1-P2 <<>> alma-laboratorios.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25362
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;arquibailleres.com.        IN    A

;; ANSWER SECTION:
arquibailleres.com.    604800    IN    A    127.0.0.1

;; AUTHORITY SECTION:
arquibailleres.com.    604800    IN    NS    ns.arquibailleres.com.

;; ADDITIONAL SECTION:
ns.arquibailleres.com. 604800 IN    A    10.200.9.168

;; Query time: 0 msec
;; SERVER: 10.200.9.168#53(10.200.9.168)
;; WHEN: Mon Jan  3 19:08:01 2011
;; MSG SIZE  rcvd: 88

I have rented a static IP address, but still when looking for my global address I see: 201.130.192.159.

To  me it looks like it is working, but I already mentioned that my  understanding of that stuff is really poor, I have finally ran the "port  scan tool" under System -> Administration -> Network Tools and it  indicates that my port 53 is assigned to "domain" and open, also port  80 is open for www.

Guys, for a learning experience it has gone  too far. I need to see some light and am really stuck and out of  possibilities. My knowledge and experience with Linux is not as long nor  deep as I would like it to be therefore I am looking for some experts  to show me the way.

Any help will be really appreciated.

Thanks.

---

### Post by bodhi.zazen on 2011-01-03
You probably do not want to do any of that.

You have a public , static ipaddress ? You then purchase a domain name, from godaddy or dyndns or wherever.

[http://www.dyndns.com/](http://www.dyndns.com/)

You do not have the knowledge to run bind, and you do not have the privilege (permissions) to upload DNS information to the "big boys", so bind will only perform local DNS.

An easier tool for local DNS is dnsmasq, but that is  not what you want.

Once you are up and running, you can learn bind in your free time, if you so desire.

---

### Post by hawkmage on 2011-01-03
You are resolving arquibailleres.com to the IP address of the loopback interface.  

In /etc/bind/named.conf.local you have: zone "arquibailleres.com".  Then in /etc/bind/db.arquibailleres.com you have "@       IN      A       127.0.0.1", the "@" is replaced by the name of the zone so in this case you have defined arquibailleres.com to have the IP address of 127.0.0.1.  

So any time you try and access arquibailleres.com you will get the localhost which usually works if you are the system running the service but if you are on a different system you try and access the system you are on.  

I assume that you want "arquibailleres.com", "ns.arquibailleres.com" and "www.arquibailleres.com" to all resolve to 10.200.9.168.  If so try this in the db.arquibailleres.com file:
@       IN      A 10.200.9.168
ns IN CNAME @
www IN CNAME @

---

### Post by 1clue on 2011-01-03
Assuming that your DNS works properly locally, you are missing a couple things:

First, you need to buy the domain name you're using.  It's currently unregistered.  Network solutions is the domain registrar I've gone with pretty much since it was the only thing around when I started, but there are dozens of registrars.  I recommend you find a reputable place.

Next, you need to register your DNS server as the authoritative domain with your domain registrar.

Third, set up your router to route the 201.130.192.159 address over to the 10.200.9.168 address.

10.200.9.168 is a private address.  It will never route on the Internet.  You need to have your router translate it.  On a cable modem you can wind up with almost any word for it.

You will also need to have DNS requests translated by the router -- either that or use a different name internally than externally.  You don't want to go there, it is a HUGE pain and if you're trying to learn how it's done then that ain't it.  Most business routers will have a setting that translates DNS requests for statically mapped IP addresses automatically, that's what you need.  Your Linux box could do it.

Your firewall/router needs to pass DNS traffic and HTTP traffic, but only allow the specifics you need.

Finally, you will probably want to get an account on a free DNS service to mirror your domain.  [www.zoneedit.com](www.zoneedit.com) is the one I use.  I have no affiliation, it's just a free DNS that has been pretty trouble-free for most of a decade for me.  If you lose your Internet connection, the DNS requests will error out.  If one of those is a caching nameserver then it seems as though it will store the error rather than trying again.  Which means your connection might be down for a few seconds and the remote DNS might be down for hours or days.

Having an external caching DNS authorized by your DNS will make sure that both the internal network and your external network have consistent DNS.  Your caching DNS will need to be authorized by your domain registrar as a secondary DNS.

---

