---
title: "Hosting web site from home"
date: 2011-02-25
forum: General Help
---

### Post by dado prso on 2011-02-25
Hello,

1) should questions about websites be posted here or the therver platform forum?

2) I'm trying to host a website from an old computer I have. I'm running Ubuntu 10.04; I have installed the LAMP package. I've made it's ip address static on my router (linksys WRT160nv3). I can ssh into it from my desktop on the same home network. 

I've been following this guide: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

Now, I'm trying to make the server public. I've set up DMZ on my router to forward to my server's local ip address.

So now, after going to whatsmyipaddress.com, I can log onto my server from my desktop, which is on my home network, but not anywhere else. 

I'm fairly sure that my ip address from my ISP is dynamic, but it hasn't changed in the last hour.....

Let me know if you need anymore details.  I'm very new to all of this.

Thanks!
Dado

---

### Post by GWBouge on 2011-02-25
One issue I've had in the past is that my ISP was kicking back requests on common ports, such as port 80 for a web host (that's for business plans!).  Might be worth changing Apache's listening port to see if that's an issue.

---

### Post by An Sanct on 2011-02-25
I agree wiht GWBouuge here, my ISP (without notice, "for the customers security") even turned off standard email ports, those where used by trojans and other ports for botnets... besides, DMZ is cool, just you don't want that on a dedicated server, port forwarding is more specific, so from the router forward port 80 to that IP, also include other wanted ports and shutdown demilitarized zone, its dangerous (one computer without NAT ... totally vulnerable!)

---

### Post by HermanAB on 2011-02-25
Howdy,

You need to get a 'server' account from your ISP (typically about $10 extra per month).  Otherwise you need to run Apache on a different port, eg 8080 and then you need to type [http://ipaddress:8080](http://ipaddress:8080) into your browser.

---

### Post by thecamelcoder on 2011-04-18
Hey mate, if your looking for a place to house your website in the cloud let me know. I have a few VPS's with plenty of free space for nix. 

I'll help with the installation as well if needed. 

Let me know at [http://www.linux-geek.co.nz](http://www.linux-geek.co.nz)

):P

---

