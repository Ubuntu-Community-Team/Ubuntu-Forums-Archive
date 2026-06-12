---
title: "SSH connection refused"
date: 2009-07-09
forum: General Help
---

### Post by LeboyX on 2009-07-09
I've been trying for the past few days to try and set up an account on dyndns.com to ssh into my Linux machine. However, when I try to ssh into it, I'm told that a connection to port 22 has been refused. The domain is working: ping'ing it works just fine. 

When I try to ssh to "127.0.0.1" or "localhost", the connection goes through just fine. 

I've got a Linksys router that I'm connected to, and I thought that a firewall within the router might be screwing with me. However, when I bypassed the router and connected straight to my modem, I received the same error.

---

### Post by jonobr on 2009-07-09
Im thinking if your getting a connection refused, and its working on your local ystem its getting blocked somewhere

The one thing I would try is open a terminal and do a packet sniff


tcpdump -vvv -i any port 22

try your ssh, if you dont see anything then the problem is away from your server,
if you see something, then its something up with the server

---

### Post by prem1er on 2009-07-09
If sshing works within the localhost and you are able to ping your machine, than the only thing else that could be causing the problem is a firewall on the machine or some hardware between the machine and the outside (router).  Are you running any firewall software on your machine, or do you have iptables set up?  Plug your router back in and try to forward port 22 to your machines local ip address.

---

### Post by LeboyX on 2009-07-09
I gave the tcpdump a go, and watched an endless stream of output flood the terminal. I did an ssh while this was going on, but couldn't distinguish anything in the output.

EDIT: @prem1er - I'm unaware of a software firewall on my machine: I haven't gone to the trouble of setting one up, but I don't know if there's one there already. I'm a bit new to this, so iptables is still a foreign term to me. How should/can I go about forwarding port 22?

---

### Post by amingv on 2009-07-09
Many DSL/cable modems have NAT (Network Address Translation), a firewall or both running.

It'd be a good idea to try and enable port forwarding for your linksys router on port 22 (Look for configurations for NAT, IP Masquerading or Port Forwarding, it varies according to make/model), and then do the same on the linksys router for your machine.

---

### Post by asmoore82 on 2009-07-09
Have you set up the router to allow connections through?

Most routers call this "Port Forwarding" or "Virtual Servers."
-OR- you could allow everything through, most
routers call this "DMZ(DeMilitarized Zone)" or "Static NAT."

Most likely when you took the router out of the situation,
you computer got a different IP from your ISP - did you
update that in dyndns? It's also possible that your router
now has a different IP since you re-connected it.

And lastly, if you have DSL, most of those boxes have
an NAT firewall in them that must be configured as well.

---

### Post by prem1er on 2009-07-09
Most likely it sounds like a firewall on your hardware.  Have a look at this website.  It will walk you through how to set up portwarding on your router.  Select your router and follow the instructions to allow SSH.


[http://portforward.com/](http://portforward.com/)

---

### Post by LeboyX on 2009-07-09
Great site, prem1er. Looks like everything's right there for me. However, the only hitch is that it details how to get a static IP address for windows users...I'm running Ubuntu 9.04. How would I go about this in Linux?

---

### Post by prem1er on 2009-07-09
Do a google search for this. There are many examples. Don't forget to back up any file that you are going to edit before you change them.  Here is a decent example.  Also, if your ISP changes your external IP address every so often (as mine does) you need to set up your router to report that to dyndns.  I can't remember the exact setting for the router off of the top of my head, so maybe someone else can help you with that. If not I will let you know when I get home.  Good luck.

[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

Edit: I think the service is called DDNS (Dynamic DNS) on your linksys router.  It should be set to disable by default.  If you enable it, you will be able to add your dyndns account to your router and then if your ISP changes your external IP address it will resolve correctly.

---

