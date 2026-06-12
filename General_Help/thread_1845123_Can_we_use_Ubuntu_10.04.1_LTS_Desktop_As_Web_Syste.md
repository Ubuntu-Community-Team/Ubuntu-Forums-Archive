---
title: "Can we use Ubuntu 10.04.1 LTS Desktop As Web System with a hundred of concurrent user"
date: 2011-09-16
forum: General Help
---

### Post by sam_ochiai on 2011-09-16
I'm a novice user. I hava Ubuntu 10.04.1 LTS Desktop installed into a embedded machine. My question is it can be used as web system( including Apache HTTP Server, Apache Tomcat, and MySQL ) accessed from a haundred of clients concurrently.

Now I have a performance trouble with few concurrent users and slow connection establishment.

So I want to know that we can use Ubuntu 10.04.1 LTS Desktop As Web System with a hundred of concurrent users? If so, I want to know the tuning points such as ulimit parameters.. Now these are default parameters.

Thanks in advance.

---

### Post by seawolf167 on 2011-09-16
Yes it will work on a sufficiently powerful computer for what services you want to offer (you need the base hardware for your use else its like putting a Golf Cart engine under the hood of a Ferrari...)

I would highly suggest using the server version instead. It is supported for longer, doesn't have a GUI to take up CPU cycles or create additional security issues. For a good web-interface to manage your server I suggest using [Webmin]("http://www.webmin.com/index.html")

---

### Post by sam_ochiai on 2011-09-16
Hello,

Thanks for your response.:KS

I understand that using Ubuntu 10.04.1 LTS Desktop as web system with a hundred of concurrent clients is no problem. My suffering problem, that is performance problem, comes from H/W or N/W platform including the configuration, does'nt it?  The PC spec is below;

CPU is Intel Core Duo2 2.4GHz
Memory is 1GB.
Two NIC (2 Ehternet card)
Network is 100Mbbs. 

Do you have any advice on performance tuning point?

Thanks again.

---

### Post by seawolf167 on 2011-09-17
If you will have a couple hundred clients connected to your server you will need a lot more horsepower than the specs you provided in your last post. I would strongly consider looking at a hosted solution through an existing company where they provide the hardware, bandwidth, etc. and you set up your services.

You can't really tuning that will matter with your PC specs - 1GB RAM isn't enough to do any page caching, also assuming you only have a single 7200 rpm hard drive, seeking will be very slow versus a raid array with SCSI drive. You may want to hop over to the Hardware subforum and ask for advice on building a webserver if this is the route you want to go (versus a hosted solution).

---

### Post by sam_ochiai on 2011-09-19
Many thanks.

The problem is configuration of iptables, that enables security setting of syn flood protection, so it makes opening a TCP connection slow.

Thanks.

---

