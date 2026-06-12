---
title: "bind9 and multiple domains"
date: 2009-07-18
forum: General Help
---

### Post by zeek333 on 2009-07-18
Hi i just wonder how to configure bind9 if i have for example 500 domains? do i need to make master zone for each domain, if so what hapen if i will need to do some changes or there is some other way to do all this simple?

---

### Post by zeek333 on 2009-07-18
P.S  example: named.conf.local  i have 500 zones
[I]zone "example1.com" {
	type master;
	file "/etc/bind/example1.hosts";
	allow-transfer { 1.2.3.4; };
};
[/I][I][I]zone "example2.com" {
	type master;
	file "/etc/bind/example2.hosts";
	allow-transfer { 1.2.3.4; };
};[/I][/I]

[I]etc. till 500 :)

then each of zoene have own zone file. 500 zones 500 zone files ??? 

how to set uder 1 file ? 

[/I]

---

### Post by zeek333 on 2009-07-24
I just tried like this an it's working but don't know is this is right. 
1 zone file for all zones

```
 $TTL    604800
 @    IN    SOA    ns3.example.com. admin.example.com. (
             2006081403
             28800
             3600
             604800
             38400 )
 @       IN      NS      ns3.example.com.
 @       IN      NS      ns4.example.com.
 ns3.example.com.      IN      A       217.0.0.1
 ns4.example.com.      IN      A       217.0.0.2
 
 example.com.    IN    A    217.0.0.3
 www.example.com.    IN    CNAME    example.com.
 mail.example.com.    IN    A    217.0.0.4
 example.com.    IN    MX    10 mail.example.com.
 
 example2.com.    IN    A    217.34.0.3
 www.example2.com.    IN    CNAME    example2.com.
 mail.example2.com.    IN    A    217.0.0.4
 example2.com.    IN    MX    10 mail.example2.com. 

etc


```

I've been reading a lot about bind9 now and I still can't understand when I have master/slave should I edit both separate or slave should take all zone files automatically. I mean if I add a new zone should I slave fetch it out from master.

---

