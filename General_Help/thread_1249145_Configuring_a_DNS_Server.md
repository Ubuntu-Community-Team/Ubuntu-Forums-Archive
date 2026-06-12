---
title: "Configuring a DNS Server"
date: 2009-08-25
forum: General Help
---

### Post by simeon.mattes on 2009-08-25
Hi everybody,

Although this topic has already been posted and I have found many things on how to configure a dns server, I can't solve my problem, since I don't know with what keywords I should search it for. Actually, it's the first time I'm trying to configure a DNS server, so please forgive my ignorance.

What I would like to do is the following:

Web Server: 147.20.39.2
DNS Server: 147.20.39.2

(they are in the same machine)

website1: site1 => 147.20.39.2/site1
website2: site2 => 147.20.39.2/site2

What I want is to configure the dns server so as to redirect me to he appropriate site every time i have the following urls

site1.mydomain.com =>147.20.39.2/site1
site2.mydomain.com =>147.20.39.2/site2


Thanks in advance

---

### Post by llebegue on 2009-08-25
This more an Apache configuration than a DNS configuration. Try to look at virtual host in Apache

---

### Post by sefs on 2009-08-25
Name-based Virtual Hosting is what you need...

[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

Then create some A records for each of those virtual domains in Bind. for your mydomain.com zone.

An example of zone configuration in bind ... [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)  ... google will likely find you more.

---

### Post by simeon.mattes on 2009-08-25
Thanks for your reply,

Sefs, the link for apache you have written is for v. 1.3 and I have 2.0.55. Is there backward compatibility?

Nevertheless, I'll check it out.

Thanks again

---

### Post by sefs on 2009-08-26
> **simeon.mattes said:**
> Thanks for your reply,

Sefs, the link for apache you have written is for v. 1.3 and I have 2.0.55. Is there backward compatibility?

Nevertheless, I'll check it out.

Thanks again

Version 2
-----------
[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html)

---

