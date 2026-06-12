---
title: "Complete DNS setup"
date: 2009-10-04
forum: General Help
---

### Post by LinuxN00bz on 2009-10-04
Hi everyone, you now have a total Linux noob here - Im too used to windows and although ubuntu seems to be quite easy to figure out, I'm finding out DNS is being a pain in the butt (first time setting up DNS):confused:.

So I'm trying to setup DNS.

**I am using**:

Ubuntu 9.04 Server
Webmin (latest version 1.490)

**I can**:

I can access the sites I created via [http://localhost](http://localhost) and [http://localhost/](http://localhost/)**folder_name**/

Since I installed mod_security However I cannot access the sites using [http://127.0.0.1](http://127.0.0.1) and [http://127.0.0.1/](http://127.0.0.1/)**folder_name**/ - I get the message "***Bad Request**  Your browser sent a request that this server could not understand.*" I'm not sure if this is important.

The sites work fine in all respects using [http://localhost](http://localhost) php/mysql/mod_rewrite etc...

**I have**:

In my Netgear router (WGT624v4) I put port forwarding to                   

**#**** | ****Service Name |                Start Port**** | ****End Port**** | ****Server IP Address               **
1-------webserver------------80--------------80-------------192.168.1.3

My domain that I am testing is pointed to my static ISP IP.

I created a master zone in the *bind dns server* using mydomain.com and used the IP 192.168.1.3 everytime I needed to enter an IP (should I?).

In the virtual server for the site under   *Alternate virtual server names *I have: [www.mydomain.com]("http://www.mydomain.com") and mydomain.com.

But mydomain.com won't resolve.

I've followed some guides but they just don't work.

Help please - call me noob if you like lol - I have a feeling I'm totally messing up...

---

### Post by doas777 on 2009-10-04
is the client correctly configured to use that dns server?
it's a little unclear to me why you need a bind server. what clients will be using it?

---

### Post by LinuxN00bz on 2009-10-04
> it's a little unclear to me why you need a bind server. what clients will be using it?


I assumed that is what one would use for DNS, basically I'm trying to run a few sites for the public Vbulletin and so on.

---

### Post by doas777 on 2009-10-04
> **LinuxN00bz said:**
> I assumed that is what one would use for DNS, basically I'm trying to run a few sites for the public Vbulletin and so on.

well if you want people like me to be able to resolve your site, you need to get your dns registered in all the public dns servers so that the one my isp uses knows your url.

setting up your own server will not help the public find your url because they are not configured to use your server. what you are setting up is a private dns server, not a public one.

look on a search engine for dns registrar services like tucows etc.you will have to pay them for the name registration (though it may not be much). alternatively you can look into a dynamic dns registration with a provider like dydns.

---

### Post by LinuxN00bz on 2009-10-04
I use Namecheap.com and have forwarded the domain name to my static ISP IP using their system interface, this setup worked when using windows server 2008 and the name resolved publicly to my site but won't with linux.

I know that setup is probably not ideal or proper but ATM I'm only messing about and try to get to grips with linux and the basics.

---

