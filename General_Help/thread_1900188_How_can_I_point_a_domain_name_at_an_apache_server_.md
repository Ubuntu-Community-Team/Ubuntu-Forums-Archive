---
title: "How can I point a domain name at an apache server running on a port other than 80?"
date: 2011-12-25
forum: General Help
---

### Post by sirspazzolot on 2011-12-25
Apache is running on port 46464 and I can see my page when I type my IP: port and everything works fine. I bought a domain name through namecheap and promptly learned that I can only point an A record at a bare IP address, no ports can be specified, and since apache isn't on port 80, that won't fly. I can get to my landing page if I use their URL Frame option to point the domain at my IP: port, but then I can't access any other pages or services on that IP through the domain name (it points to my landing page, no matter what comes after mydomain.com). I'm not able to use port 80. Does anyone know how I'd go about pointing my domain name at my server?

---

### Post by azmyth on 2011-12-25
You can use something like no-ip.biz to forward your URL.

---

### Post by sirspazzolot on 2011-12-25
any sort of url forwarding isn't going to help. URL forwarding is essentially what I'm already doing. I tried it with no-ip and I'm getting the same problem. I think what I've gotta do is effectively point an A record at a specified port, which isn't possible. I guess I could try to make port 80 usable. For now, I'll just redirect to the ugly looking IP: port.

---

### Post by cybergalvez on 2011-12-25
if you are behind a router/firewall you could open port 80 on the router and have it point to port 46464 on your computer

---

### Post by sirspazzolot on 2011-12-25
like I said, I'm not able to use port 80. mummy dearest has a creepy-*** live stream of our living room and the camera crap uses port 80, so I'm not allowed to. I might try to play around with that and figure out how to change ports.

---

### Post by sirspazzolot on 2011-12-26
Would I be able to do something with an SRV record? there's a spot for them at the bottom of the configuration page. mine is
_http . _tcp 1 1 46464 mydomain.com
(service.protocol priority weight port target)

it seems to not do anything though. if I understand it correctly, the srv record is supposed to point to an a record?

---

### Post by lisati on 2011-12-26
The paid version of no-ip has a port redirection service.

---

### Post by sirspazzolot on 2011-12-26
it's too much money for something I'm just doing for kicks. I guess I should just give up until I can use port 80, or get a cheap vps or something...

---

### Post by Habitual on 2011-12-26
Point the A record at your machine and configure Apache[2] to handle the port using a/the <VirtualHost> directive.

[http://www.wowtutorial.org/tutorial/24.html](http://www.wowtutorial.org/tutorial/24.html)

---

### Post by sirspazzolot on 2011-12-26
my problem is that I can't point my a record at my machine, since there is some other thing using port 80.

---

### Post by Habitual on 2011-12-26
> **sirspazzolot said:**
> my problem is that I can't point my a record at my machine, since there is some other thing using port 80.

Dude, the _***port doesn't matter***_ for the A Record.

---

### Post by sirspazzolot on 2011-12-26
that's the problem, bro. my understanding is that it's not just that ports don't matter, it's that the concept of ports does not exist. they're a different level of networking. and since I can't specify a port, anything going to my external IP address is going to port 80 and to the creepy camera in my living room instead of my server. the camera is its own entity, it is in no way related to my server, so virtual hosts won't really help me out here since I'm not getting the traffic to that machine in the first place. if I'm misunderstanding something in here, feel free to correct me.

edit: tangently related question: when I point an a record at my bare ip, it gives the stupid thing. but if I do domain.com:46464, instead of giving me my page thing, it just doesn't load anything. why might that be? isn't domain.com:46464 the same thing as my-ip:46464?

---

### Post by Habitual on 2011-12-26
DNS handles the IP by sending nameserver A Record entry to the client/requestor and then the Request is routed to your machine and then is handed off to Apache to serve up the VirtualHost/Port

Apache handles the IP/Port using VirtualHost directive. (This is rather generic)
```

    <VirtualHost *:46464
     ServerName MyCoolDomain.com
    DocumentRoot FULL_PATH_TO_MyWebPage
    </VirtualHost>
```Don't forget to restart apache after making changes.

Same way IP:80 works with an SSL Cert on IP:443.
Same host, different ports.
You _could_ have 1000 VirtualHosts on a the same IP.
You *could* have 500 VirtualHost directives on 500 different ports,  or
you **can** have 1 camera on one port and your content on 46464


Personally, even after 18 years in the business, I still struggle with VirtualHosts,

Sometimes I suck at explaining even the simplest of concepts (Ima dork) but don't be discouraged, there are smarter people than I reading this thread and they will jump in and reply. :)

Termimal >
```
sudo lsb_release -drc
```and apache version please.

---

### Post by sirspazzolot on 2011-12-26
I'm on oneiric, using the latest version of apache2 from the repositories.

I figured my configuration files were kind of a mess from me screwing around a lot so I decided to uninstall apache2, delete /etc/apache2 and /var/www and reinstall apache2. but reinstalling it isn't creating /etc/apache2 or /var/www so I guess I'm kind of screwed. imma try compiling it from source I guess, then I'll give the virtualhost thing a shot. source from website is 2.2.21

---

### Post by sirspazzolot on 2011-12-26
compiling from source didn't create /etc/apache2 either. lolol. I'm so confused.

---

