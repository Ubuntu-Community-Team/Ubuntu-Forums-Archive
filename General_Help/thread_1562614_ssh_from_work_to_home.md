---
title: "ssh from work to home"
date: 2010-08-27
forum: General Help
---

### Post by l3ecl on 2010-08-27
I'm having some problems trying to ssh from work to home.

I can ssh from my home laptop to my home desktop but I can't ssh from my work to my home desktop. The problem seems to be on my desktop since I can ssh from work to anywhere else. The IP address I type alawys results in network connection timed out. 

I hope this is a common problem with a common solution =\

---

### Post by surfer on 2010-08-27
did you install the ssh server on the home machine?
do you have a router at home?
if so, did you enable port forwarding?

that's all i can think of at the moment. or could you be more specific about your setup?

---

### Post by holiday on 2010-08-27
> **l3ecl said:**
> I'm having some problems trying to ssh from work to home.

I can ssh from my home laptop to my home desktop but I can't ssh from my work to my home desktop. The problem seems to be on my desktop since I can ssh from work to anywhere else. The IP address I type alawys results in network connection timed out. 

I hope this is a common problem with a common solution =\

It's possible your work firewall is blocking you. Is "anywhere else" your company's or clients' servers?

Or it could be your home firewall...

Or - yes - port forwarding. That's probably it. What's the error coming back?

---

### Post by Iowan on 2010-08-27
Besides port-forwarding from router to machine, you need to know current "external address" for router. Unless you have a static address from your ISP, you may need a service like [no-ip.com]("http://www.no-ip.com/newUser.php") or [dyndns.com]("http://www.dyndns.com/").

---

### Post by crazyguy510 on 2010-08-27
If its connection refused then its probably an incorrect IP  address or you didn't install the server. 

I'd follow the suggestions above and let us know what you get.

---

### Post by l3ecl on 2010-08-28
Caveat: I'm cluless when it comes to networking 

> **surfer said:**
> did you install the ssh server on the home machine?


I think ssh server is installed. I ran the command 

```
sudo apt-get install openssh-server
```and it says it is already the newest version. I am an absolute beginner in these matters, is having it installed enough or do I have to run it? (I hope this question wasn't too stupid of a question :D)

I ran 

```
netstat -tulpn
```> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:53369           0.0.0.0:*  so I guess my computer is listening?

> **surfer said:**
> 
do you have a router at home?
if so, did you enable port forwarding?


I don't think I have a router. Technically I don't even know what a router means. I do have all 3 of my computers connect wireless to a network for internet.  If i type ifconfig

> comp1 has an "inet addr" of 172.xx.x.33
comp2 has an "inet addr" of 172.xx.x.34
comp2 has an "inet addr" of 172.xx.x.35  Hope this helps if not tell me what commands to run

---

### Post by l3ecl on 2010-08-28
> **holiday said:**
> It's possible your work firewall is blocking you. Is "anywhere else" your company's or clients' servers?

Or it could be your home firewall...

Or - yes - port forwarding. That's probably it. What's the error coming back?

 I really doubt it is my work's firewall. How do I find out if it is my home firewall blocking me? 

As for the error. When I try to connect via putty, it just says connection timed out. I can't even type the username to login as.

---

### Post by l3ecl on 2010-08-28
> **Iowan said:**
> Besides port-forwarding from router to machine, you need to know current "external address" for router. Unless you have a static address from your ISP, you may need a service like [no-ip.com]("http://www.no-ip.com/newUser.php") or [dyndns.com]("http://www.dyndns.com/").

In order to ssh from my laptop to desktop, I run ifconfig on my desktop, copy wlan0's inet addr, and then i go back to my laptop and ssh into whatever address it gave me. 

I just can't seem to do this from same thing when I want to connect from work.

---

### Post by Asmodai on 2010-08-28
The router is a little box somewhere in your house that connects to the internet.
Your computers just communicate with the router, they don't access the internet directly.

Run route -n and type the last IP address that shows up into your browser.
That should get you on your router's web interface.

---

### Post by Zeobak on 2010-08-28
> **l3ecl said:**
> In order to ssh from my laptop to desktop, I run ifconfig on my desktop, copy wlan0's inet addr, and then i go back to my laptop and ssh into whatever address it gave me. 

I just can't seem to do this from same thing when I want to connect from work.

Yeah, it's not your work firewall, I can tell you that.  Most places (all places) allow outgoing port 22 connections.  Enable logging on your router and watch what it denies.  Also tail your /var/log/syslog to see if it denies any incoming connections due to an iptables config, which can happen if you use guarddog or something to use scripts to set your firewall rules.

You might be using the wrong IP address; try connecting to whatever your router reports as the DHCP address, or try using whatever is reported on a site like "what is my ip dot com".

If your ports are open, you might have something else going on:

try, instead of sudo apt-get install openssh-server, sudo apt-get install ssh

Then make sure it's an enabled service, but it should be enabled when you apt-get it

---

### Post by Zeobak on 2010-08-28
> **l3ecl said:**
> I really doubt it is my work's firewall. How do I find out if it is my home firewall blocking me? 

As for the error. When I try to connect via putty, it just says connection timed out. I can't even type the username to login as.

I missed this post earlier.  Here's what's up:  if you don't know how to find out if your router is blocking it,

your router is blocking it.

Configure your router to forward port 22 TCP requests to whatever IP address your router reports that it has given your client.

It's all there in your router configuration, which is accessible over the web and is often reachable by browsing to [http://192.168.100.1](http://192.168.100.1)

---

### Post by Zeobak on 2010-08-28
Sorry, friend, forgot to say:

router = wireless base station thing

So just configure your wireless base station thing (router) to forward incoming port 22 TCP requests to your 172.x.x.35 address or whatever your pc is, port 22.

edit:  then connect by using putty or whatever to go to your router's ip address.  The piece of information I think you're missing is that your router has an ip address.  This is an internet-facing, "real", "accessible" address.  Your router gives your three computers .35, .36 etc their own "internal" or "nonaccessible" addresses.  It hides and protects your computers.  If your router gets a request on port 22, it's going to deny it unless you specifically tell it, "no, send port 22 traffic to my pc at this internal address."  Easy peasy!

---

### Post by l3ecl on 2010-08-28
> **Zeobak said:**
> Sorry, friend, forgot to say:

router = wireless base station thing

So just configure your wireless base station thing (router) to forward incoming port 22 TCP requests to your 172.x.x.35 address or whatever your pc is, port 22.

edit:  then connect by using putty or whatever to go to your router's ip address.  The piece of information I think you're missing is that your router has an ip address.  This is an internet-facing, "real", "accessible" address.  Your router gives your three computers .35, .36 etc their own "internal" or "nonaccessible" addresses.  It hides and protects your computers.  If your router gets a request on port 22, it's going to deny it unless you specifically tell it, "no, send port 22 traffic to my pc at this internal address."  Easy peasy!

perfect post!!
you nailed it! i got it working and really awesome explanation in layman's terms.

---

