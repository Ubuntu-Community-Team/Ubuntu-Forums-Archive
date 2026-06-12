---
title: "The best dynamic IP address service"
date: 2011-03-20
forum: General Help
---

### Post by nbv4 on 2011-03-20
I have a dynamic IP at home. I want to have a domain that I can use to access my home computer. There are a lot of services like dyndns that do this. The way these services work is by running a program on your computer that phones home your current IP. These programs have a tendency to be crappy and/or windows only.

Whats the one that works the best in ubuntu?

---

### Post by WorMzy on 2011-03-20
My router has a built in function which alerts DynDNS to a change in IP address as and when it happens.

I've also used No-IP, which runs the way you describe. It occasionally worked, but there were a number of occasions where it didn't update without me forcing the daemon to restart, and even then it only updated sometimes.

So I guess I recommend DynDNS, although I've never used it the way you've described.

---

### Post by oracle2b on 2011-03-20
Somebody already worte himself a script to solve this problem [here]("http://blogger.ziesemer.com/2010/01/dyndns-update-client-shell-script.html"). but the router config is far better in the long run.

---

### Post by gandaran on 2011-03-20
> **nbv4 said:**
> I have a dynamic IP at home. I want to have a domain that I can use to access my home computer. There are a lot of services like dyndns that do this. The way these services work is by running a program on your computer that phones home your current IP. These programs have a tendency to be crappy and/or windows only.

Whats the one that works the best in ubuntu?
I used to have 'ddclient' installed before I bought the router and it worked very well with my multiple dyndns domain names something my router doesn't, the router only supports one dyndns domain name.

---

### Post by Locke_99GS on 2011-03-20
I've used this to update dyndns in the past, and it worked well: [http://freshmeat.net/projects/inadyn](http://freshmeat.net/projects/inadyn)

---

