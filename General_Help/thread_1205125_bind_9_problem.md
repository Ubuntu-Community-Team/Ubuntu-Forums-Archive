---
title: "bind 9 problem"
date: 2009-07-05
forum: General Help
---

### Post by zeek333 on 2009-07-05
Hi;

my settings: 

FQDN example.com
dns and lamp are set on 10.0.0.125
my porvider ip is 123.123.123.123[FONT=monospace]
[/FONT]123-reg.co.uk nameserver ns1 is set on 123.123.123.132
in router i set forwared for dns port 53 and web port 80
 

when i checked my web form outside it works with [http://123.123.123.123](http://123.123.123.123) (provider ip) but don't work when i type in [www.example.com]("http://www.example.com/"), when i ping [www.example.com]("http://www.example.com/") it shows me 10.0.0.125 (ip which i setup for my dns) 

please help!!!

---

### Post by blueridgedog on 2009-07-05
Your DNS needs to list the external IP, not the internal one.  If you give the domain name, I can run a dig on it from the outside (real IPs would help as well).

---

### Post by zeek333 on 2009-07-05
this is my zone file: 

$TTL    604800
example.com.       IN      SOA     ns3.example.com. admin.example.com. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
example.com. IN MX 10 mail.example.com.
 
example.com.       IN       NS      ns3.example.com.
example.com.       IN       A       10.0.0.125
ns3                      IN       A       10.0.0.125
www                    IN       A       10.0.0.125
mta                     IN       A       10.0.0.125

did u mean instead of 10.0.0.125 i must write 123.123.123.123 ?

---

### Post by blueridgedog on 2009-07-05
yes.  You can't give out 10 dot addresses to the real world.  Your name server has to give out the public IP (which you have forwarded in to your server).

---

### Post by zeek333 on 2009-07-05
ok i understan that but whats happen when i have 1 external ip an 2 dns servers how can i set master and slave then?

---

### Post by blueridgedog on 2009-07-05
The slave DNS server will pull a copy of the DNS file from the master, and will resolve URLs to the same IPs.

---

### Post by zeek333 on 2009-07-06
is it in my case it should look like this? 
zone "example.com" {
        type master;
	file "/etc/bind/db.example.com";
        allow-transfer { 10.0.0.125; };
};

zone "example.com" {
	type slave;
        file "db.example.com";
        masters { 10.0.0.126; };
}; 

btw thanks my domaind showed up now.

---

### Post by blueridgedog on 2009-07-06
If the two machines are on your internal network and can communicate via the 10 net ip addresses, then yes, but if they are on the public network, you will need to use the public IP addresses that have been reverse mapped to them.

---

