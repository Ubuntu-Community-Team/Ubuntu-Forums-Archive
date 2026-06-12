---
title: "DNS Issues"
date: 2010-07-16
forum: General Help
---

### Post by DrDoS on 2010-07-16
I have been trying to figure out for the past 2 days why my zone files are not
updating with the DNS servers. Both my servers are my name servers for my
websites. 

208.122.229.58 NS1.REFLECTSTUDIOS.COM
208.122.229.59 NS2.REFLECTSTUDIOS.COM

.58 was not running a name server up until yesterday so I correct that issue
and installed bind and xfersd over all the zone files from NS2.

Now my issues is that none of my zone files are being updated. 

I update them just fine locally - and check them with named-checkzone and they
check out fine.

Here is an example zone file.

```
$TTL 14400
@      86400  SOA    ns1.reflectstudios.com.
CMPRB2.custommyspaceprofiles.com.(
                                1016
                                86400
                                7200
                                3600000
                                86400
                        )
faithinink.com. 3600    IN      NS      ns1.reflectstudios.com.
faithinink.com. 3600    IN      NS      ns2.reflectstudios.com.

localhost.faithinink.com.      14400  IN      A      208.122.229.59

@      14400  IN      A      208.122.229.59

ftp    14400  IN      CNAME  @
www    14400  IN      CNAME  faithinink.com.
admin  14400  IN      A      208.122.229.59

faithinink.com.    14400  IN      MX      10      ASPMX.L.GOOGLE.COM.
faithinink.com.    14400  IN      MX      20      ALT1.ASPMX.L.GOOGLE.COM.
faithinink.com.    14400  IN      MX      20      ALT2.ASPMX.L.GOOGLE.COM.
faithinink.com.    14400  IN      MX      30      ASPMX2.GOOGLEMAIL.COM.
faithinink.com.    14400  IN      MX      30      ASPMX3.GOOGLEMAIL.COM.
faithinink.com.    14400  IN      MX      30      ASPMX4.GOOGLEMAIL.COM.
faithinink.com.    14400  IN      MX      30      ASPMX5.GOOGLEMAIL.COM.

```

Now the serial number for this on my local copy is    1016 since I have applied
many changes to it but when I run the following tool 

[http://www.zoneedit.com/lookup.html?host=faithinink.com&type=SOA&server=&forward=Look+it+up](http://www.zoneedit.com/lookup.html?host=faithinink.com&type=SOA&server=&forward=Look+it+up)

the serial number is the old 1011. This I changed MONTHS ago when I added a sub
domain and yet as still not been updated. 

I was hoping one of you guys can point me in the right direction of trouble
shooting this issue here.  I need to resolve this ASAP for I have a few new
clients I need to add to my server and its not updating. 

Thank you 
- Adam

---

### Post by DrDoS on 2010-07-16
Alright Guys - I fixed the issue.

The issues was when I checked the logs the zone files WHERE NOT being loaded in from the correct spot.

I was updating my zone files in /var/lib/named/example.zone
Bind was loading my zone files from /var/cache/bind/zones

Simple mistake and costed me about 12 hours worth of work - but glad its finally now fixed. 
so If you are experience the same issues

try this

rndc reload

then 

tail /var/log/dameon.log

and see what it says under named. 
If you are getting File Not Found then you are in the same boat as me well that I was in at least.

---

### Post by Iowan on 2010-07-16
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?  ;)

---

