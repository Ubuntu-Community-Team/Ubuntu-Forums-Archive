---
title: "web hosting on home server"
date: 2012-07-20
forum: General Help
---

### Post by DK555 on 2012-07-20
Hi All
 
would anyone be able to offer some advise/help on a question I have? I have installed ubuntu server 12.04,I have install LAMP, Samba,vsftpd, signed up for a dyndns account that monitors my IP, everything is working, I can connect remotely to my home server, view files write/read etc. Its the first time I've use linux/ubuntu so was a little project and just been learning from tech files online :) . With everything up and running I wanted to understand how to host a webpage. 
 
I see in the directory /var/www this is where the files are located and there is already an index.html file in there, when clicked opens and says all installed ok and working. 
My question is;
 
Q1: How do I few the website/page remotely like a website URL?
 
When I go for example [http://www.mydomain.dyndns.com/index.html](http://www.mydomain.dyndns.com/index.html) nothing appears, on the understanding that,that is how it works??
 
Q2:What else do I need to do to be able to see a webpage from my home server remotely?
 
I appreciate any thoughts on this as this is all new to me:confused:
 
many thanks

---

### Post by cool110 on 2012-07-20
Your server will be behind a NAT router which will be dropping the incoming connections. You need to forward port 80 to the servers private IP (192.168.x.x).
You can check that the port was forwarded correctly here.
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by texpat on 2012-07-20
HI DK555,

if there is an index.html in /var/www and everything is set up correctly, it should show.

As regards 
> [http://www.mydomain.dyndns.com/index.html](http://www.mydomain.dyndns.com/index.html)
are you sure you need the www? I have a similar setup and the URL is without www.

Does the page show on your local machine with 
```
http://localhost/index.html
```

If it does locally but not remotely, you may have router configuration issues (NAT) or your firewall may be cuting off traffic.

---

### Post by DK555 on 2012-07-20
Hey there
 
Thanks for the reply!
 
oh! yes I see I have already port forward for webmin and ftp, so is port 80 for web?

---

### Post by DK555 on 2012-07-20
hey there
 
I will check if I can see the webpage when I go to 
 
```
 
http://localhost/index.html

```
 
wil keep you posted :)
 
many thanks

---

### Post by DK555 on 2012-08-05
Hi there
 
yes, when I type [http://localhost/index.html](http://localhost/index.html) I get the webpage, I have port forward 80, and then got to [http://www.mydomain.server.com](http://www.mydomain.server.com) but it does not find the webpage . . . what am I missing??

---

### Post by Cheesemill on 2012-08-05
When your browser does a DNS lookup for your site it will resolve to your external IP address, which is to be expected.

The problem is that home routers don't do port forwarding out from your internal network and then back again via your external IP (this is called packet rewriting or NAT loopback), this feature is only available on business class routers that cost a lot of money.

The way around this is to set up your network so that every time a DNS lookup is done from inside your network it will return the internal IP address of your server rather than your external IP, there are 2 ways to accomplish this:

1 - Set up an internal DNS server. Can be tricky to set up but only needs to be done once for all of the machines on your network.

2 - Add an entry to your hosts file. Easy to set up but has to be done on every machine on your internal network.

Adding an entry to your hosts file is as easy as doing:
```
gksudo gedit /etc/hosts
```Then add the following line to the bottom of the file:
```
192.168.1.100     www.example.com     www
```replacing the values with the correct internal IP address and domain name for your web server.

---

### Post by DK555 on 2012-08-05
Hey there
 
thanks for the reply, will have a go at that and let you know what happens :confused:

---

### Post by DK555 on 2012-08-05
... but if I was to access remotely from outside of my network and different pc, should it not be ok?

---

### Post by Cheesemill on 2012-08-05
> **DK555 said:**
> ... but if I was to access remotely from outside of my network and different pc, should it not be ok?

If you have your port fowarding and dynamic DNS set up properly then yes, you should be able to access your webserver by entering your domain name into a browser.

The post I made above is only relevant if your are trying to access your website by name from *within* your home network.

---

### Post by DK555 on 2012-08-05
> **Cheesemill said:**
> If you have your port fowarding and dynamic DNS set up properly then yes, you should be able to access your webserver by entering your domain name into a browser.
 
The post I made above is only relevant if your are trying to access your website by name from *within* your home network.
 
many thanks for your help! I have set up port foward, will see if I can access remotely from a pc outside my network:)

---

