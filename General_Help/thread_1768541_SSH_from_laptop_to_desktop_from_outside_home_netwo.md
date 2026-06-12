---
title: "SSH from laptop to desktop from outside home network"
date: 2011-05-26
forum: General Help
---

### Post by krumpy on 2011-05-26
I'm trying to SSH from my laptop to my desktop from outside our home network.  The desktop sites behind a router.  Currently I can ssh into the desktop from laptop and vice versa when both computers are on the home network.  I've looked around for a while now and I guess I'm still a little confused about how to go about doing this.

---

### Post by nemilar on 2011-05-26
Hi,

You need to use the port forwarding feature of your router.  This expose a port to the internet on your external IP (the IP that the internet sees), and forward the traffic to your desktop.

Google "port forwarding" for more information.

Please make sure that you're using a secure password!!!!!!!  I can't stress this enough.  It won't be long before a port scanner realizes that you have sshd running; once that happens, you'll see bots trying to break into your network.  As long as you have a secure password, you're fine; but if you make your password short, or a dictionary word, you'll get hacked pretty quickly.

---

### Post by spcwingo on 2011-05-26
I second what nemilar said.  The only thing that I would suggest also is to change the default listening port (from 22 to something non-standard like 2222).  If you need help doing that, just let me know.

---

### Post by krumpy on 2011-05-26
So prior to posting I had googled port forwarding and I was left a bit confused.  My router does support port forwarding and it looks super straight forward to configure.  Also, i registered with a dynamic dns provider to account for the changing external IP.  But even after looking around for a while I'm still confused about what exactly port forwarding is and the steps necessary to set it up (not much networking experience).

As far as security I disabled password logins for ssh, and well as root login (using private key only), not sure if this enough though?

---

### Post by spcwingo on 2011-05-27
Which model router do you have?  I just ask because the steps necessary to setup port forwarding differs between make/model.

---

### Post by nemilar on 2011-05-27
Hi,

To understand port forwarding, first you have to understand Network Address Translation (NAT).  The following is an incredibly simplified explanation.

Your ISP most likely only provided you, as a customer, with a single IP address.  This *public* IP address is the address that the outside world - anyone on the internet - can see.  It's the address that your router uses when it talks to servers on the internet, for example when you visit a webpage.

However, you might have multiple computers plugged into your router.  What your router will do is assign each computer on the your LAN its own IP address, typically 192.168.x.x.  These are private IPs, only visible to people inside your LAN.

When a computer on the LAN, for example, 192.168.0.100, wants to communicate to a computer out on the internet, it needs to go through the router.  The router takes the data from 192.168.0.100 and sends it along to the remote computer using your *public IP*.  When that remote computer responds, the router knows to forward the response to 192.168.0.100.

Now, if you aren't using this scheme of network address translation, you would not have to use port forwarding.  Let's say you didn't use a router, and you plugged your computer directly into your internet connection. Then your computer would have the *public IP* rather than the internal IP of 192.168.0.100 (for example).  You would simply open whatever ports you wanted, and they'd be visible on the internet to anyone.

But, because you are behind the router, you need to tell the router to listen on a port, and what to do when someone tries to talk to it over that port.  This is what port forwarding does.  You tell your router to listen on port 2222, for example, and forward all requests to 192.168.0.100 on port 22.

I hope that is clear!

---

### Post by krumpy on 2011-05-27
nemilar - thanks for the reply.  I think I understand the general stuff (like my desktops network IP  isn't my external IP), and that I need to setup my Router (Linksys  WRT400N) to forward requests to a certain port and internal IP.   However, I was hoping someone could be a little more explicit.  One question though.  I thought that ISP didn't typically assign a dedicated IP address.  Regardless registering with a service like no_ip would work either way right?  

Also, is there a way to test if this is working without leaving my home network, since I was using ssh with port forwarding earlier, but I wasn't sure that I was actually testing anything since I'm still within my home network.  Thanks again for the help.

---

### Post by nemilar on 2011-05-27
As long as you SSH to the external IP address, and not the LAN IP address, then you are testing the port forwarding.

---

### Post by nemilar on 2011-05-27
You can use a service like DynDNS to configure a URL for your dynamically-assigned IP.  You are correct - Most residential accounts get dynamically assigned IPs.  You can usually pay extra for a static IP if you need it.

There is a how-to on assigning a URL for a dynamic IP, here:

[http://techthrob.com/2009/03/02/three-steps-to-a-free-domain-for-your-home-network/](http://techthrob.com/2009/03/02/three-steps-to-a-free-domain-for-your-home-network/)

(Disclaimer: It is my how-to.)

---

### Post by kevdog on 2011-05-27
Register you domain name (free or paid) with noip.com or other such company, and use their no-ip.com dynamic updater.  That will usually keep your ip address current no matter if the IP address changes between reboots of your router as provided by you internet service provider.  You can then either SSH to the outside IP address or domain name to test.

---

### Post by krumpy on 2011-05-27
But it seemed like it worked regardless of the port I set my router to from/to.  For example my router setup has a page "single port fowarding" 

I set external port to 8956 (or something) to 22 ip 192.xxx.  

Then from my laptop I was using ssh -L 8956:externalip:22 login@desktop.

But the above command seemed to work regardless of the port i used for example ssh -L 8999:externalip:22 login@desktop worked as well.

---

### Post by krumpy on 2011-05-27
I tried above from outside network today and it didn't work.  If someone would be available to chat PM me as I think it's really close to working.  I'm guessing firewall setup?
Thanks nemilar for the dynDNS stuff that was really helpful.

---

### Post by LordNeo on 2011-05-27
[http://portforward.com/english/routers/port_forwarding/Linksys/WRT400N/SSH.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT400N/SSH.htm)

Step by Step for your router.

you should do:

ssh EXTERNALIPX:XPORTONROUTER -u USERNAME

USERNAME is only if is not the same on the computer you are on.

The router will translate the EXTERNALIPX:XPORTONROUTER to INTERNALIP:22

EDIT2: If you set port 22 both on router and on your computer (you can modify the port for ssh on your computer too) then you can just use "ssh EXTERNALIP -u USERNAME"

---

### Post by Maheriano on 2011-05-27
Holy smokes, you're all confusing this guy. Let me explain it a bit better.

You have 1 external IP and a bunch of internal IP. What that means is your IP on the world wide web is what your internet provider assigned you and is how the world sees your switch (router). Now every computer attached to your switch has its own internal IP assigned by the switch.

Let me explain this a little better. When I go to [www.whatismyip.com](www.whatismyip.com) and I get my external IP, it is something like 247.60.27.30. So when I run ```
ssh deemar@247.60.27.30
``` I get connected to my switch (and get denied) but I don't get any further than that until I forward the request to a specific computer. So I log into the switch, forward all requests on port 22 to the internal IP of my computer I want to connect to (192.168.0.199), save and log out. Now when I run the same SSH command on the external IP, it gets to my switch, the switch forwards it to the computer and I connect. Yay!

The reason it works for you on the network is because you're connecting directly to the machine on the internal IP without leaving the network so the switch doesn't have to forward anything.

So if you want to test this and see if it works while you're on your network, just use your external IP ([www.whatismyip.com](www.whatismyip.com)) and the request will go out to the web, come back to hit your switch, and your switch should forward the request through to your designated machine. Simple as that.

---

### Post by krumpy on 2011-05-29
Works great now.  My router allows for both port forwarding and supports dyndns.com.  So I really just had to make changes to the router setup.  What do people generally do for security?  

I'm currently forwarding a random high number port to port 22.  Also I disabled password login, as well as root login.  Regarding ufw it seems like you have to allow from 22 in order for things to work.  Are there any other security precautions that you should take?

---

