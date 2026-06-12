---
title: "dynamic ip on my server"
date: 2010-02-03
forum: General Help
---

### Post by oospill on 2010-02-03
Hello.  I've got Apache installed so I can learn perl and php, and to show off, of course.  I just realized last night that my IP isn't what it was three months ago.

does anyone here have any experience with a dynamic IP program (like DynIP back in the day.) .. I've seen a few options, but I was hoping someone would have some experience.

thanks!!

---

### Post by Brandon Williams on 2010-02-03
I have a dyndns hostname and use ddclient on my server to keep the dyndns DNS server up-to-date with my current address. Many home internet gateway's will handle dyndns for you automatically, too.

---

### Post by lisati on 2010-02-03
I use noip.com and a setting in my router. noip have a client to automatically update things as well.

---

### Post by Ordes on 2010-02-04
pretty normal that your public IP is dynamic.

You can:
1) sign up at any of dynamic IP registers, like dyndns.org. The basic offers are mostly free.

2) Register your own IP. Most IP registers also support dyndns, e.g. Joker.com

----
After that keep your IP register update:
1) some routers support dyndns update. Some only for certain sites, some you can configure for any site. Have to check your router

2) dyndns-update by software. ddclient, noip, inadyn, all software daemons that grap your public IP and send it to your IP register.

---

### Post by mickymanuel on 2010-02-04
Hi,
 I signed up with [www.noip.com](www.noip.com) and have found them pretty easy to use. Once you have signed up you can either put the settings in your home router or alternatively you can install a small program on your server (sudo apt-get install noip2). Either way, you just enter your noip username and password and that is it. They also have clients for windows and mac.

---

### Post by oospill on 2010-02-04
great.  thank you all for the posts!!

---

