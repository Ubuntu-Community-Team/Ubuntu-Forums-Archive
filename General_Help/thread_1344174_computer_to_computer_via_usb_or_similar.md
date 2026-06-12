---
title: "computer to computer via usb or similar"
date: 2009-12-02
forum: General Help
---

### Post by worldsayshi on 2009-12-02
Scenario: I have a small computer with Ubuntu server installed (which I intend to use as a server) and I want to be able to control it without having to use a monitor and keyboard, from my laptop for instance. I have tried ssh, which works sometimes, when it manages to connect to the network, that is.

I wonder if there is any more fail-safe solution than using ssh or telnet? Or some solution that doesn't require a working network connection. Could I use an usb cable to turn the server into a 'slave' or something similar? 

If nothing else: Any good keywords to search on?

/Thanks

---

### Post by Snow986 on 2009-12-02
Not sure if its possible to slave it, but just about everything I can think of would use the network to manage it.  Such as VNC or ssh, etc.  Maybe you could get to the bottom of why it doesn't always connect to the network, then problem solved.

---

### Post by Spectre5 on 2009-12-02
YA, I would investigate the SSH problem.  SSH is a great way to do exactly what you want...

---

### Post by hughw on 2009-12-02
it depends how much money you want to spend. you can get a kvm over ip box, but they can be quite expensive. I think it is also possible to do use console over serial,, obviously dependent on whether your laptop has a serial port.

---

### Post by StuartN on 2009-12-02
> **worldsayshi said:**
> Or some solution that doesn't require a working network connection. Could I use an usb cable to turn the server into a 'slave' or something similar?

Is there a reason that you can not use an ethernet cable between the two? It is cheap, reliable, safe and can be of any reasonable length.

---

### Post by worldsayshi on 2009-12-04
> **StuartN said:**
> Is there a reason that you can not use an ethernet cable between the two? It is cheap, reliable, safe and can be of any reasonable length.

Well, I guess not really. But if it doesn't manage to connect to the network would it be more likely that it would work via direct ethernet cable you think?

Um, I'm not that at home when it comes to networking. I've just managed to get ssh and some port forwarding to work. Well, it worked for a while at least.

I guess I have to connect a monitor to it then. To bad I threw out my last one. I only have my laptop stuck monitor left. :P

---

### Post by llamabr on 2009-12-04
You shouldn't need to do port forwarding to log in over ssh on the internal network.  Just ssh to the local ip.

Since you intend to use it as a server anyway, you'll need to get to the bottom if your networking issues eventually.  Best not to bother with all of these other work arounds, since they'll be difficult, and eventually useless.

---

### Post by worldsayshi on 2009-12-04
> **llamabr said:**
> You shouldn't need to do port forwarding to log in over ssh on the internal network.  Just ssh to the local ip.

Since you intend to use it as a server anyway, you'll need to get to the bottom if your networking issues eventually.  Best not to bother with all of these other work arounds, since they'll be difficult, and eventually useless.

I didn't port forward to make it work over the internal network. I actually made it work internally at first, and later externally as well, with port forwarding and ssh. But then for some reason it broke down and I can no longer access it via ssh, neither externally nor internally. Since I don't have a monitor any longer, plus I would rather have an alternate, more reliable(?) solution, I wonder if there is any other way to get inside it. 

Maybe I could set up some ip-handout service from my laptop, connect directly by ethernet cable to my server and ssh to the ip I just handed out?

I guess the easiest, "most error prone", way would be to get a new monitor, but I don't have any place to put it! :(

---

### Post by Snow986 on 2009-12-04
ssh should be very reliable.  If you cant get into it at all, how do you know whats going on.  Does the ssh only work intermittently or does it just not work at all?  Are you even sure its getting an ip from the router.  Can you get into your router and see it on the network?  Maybe it has renewed to a different ip?

---

### Post by StuartN on 2009-12-04
> **worldsayshi said:**
> I guess the easiest, "most error prone", way would be to get a new monitor, but I don't have any place to put it! :(

As far as I understand it, you are using a wireless-connected laptop to access the server, and the wireless is unreliable. If the server and the laptop have IP addresses, and have different IP addresses (dynamic from the router, or fixed), then plugging an ethernet cable between them will give you a perfect connection. There is no setup required whatsoever.

ssh, ssh -X or remote desktop will all work if they have been enabled on the server.

---

### Post by worldsayshi on 2009-12-05
> **StuartN said:**
> As far as I understand it, you are using a wireless-connected laptop to access the server, and the wireless is unreliable. If the server and the laptop have IP addresses, and have different IP addresses (dynamic from the router, or fixed), then plugging an ethernet cable between them will give you a perfect connection. There is no setup required whatsoever.

ssh, ssh -X or remote desktop will all work if they have been enabled on the server.

Its not that the wireless is unreliable. Its that the server suddenly stopped beeing able to connect to the router and the network. The router is (=should be) handing out a static ip to the server (based on mac adress). When I try to ssh to that adress now I get:

ssh: connect to host 192.168.0.50 port 22: No route to host

...for response. It used to work. I haven't made any changes since.

Anyway, so what you are suggesting is to, instead of going via the router, set up a direct cable between the laptop and the server? But then I would have to configure some kind of connection between them and set up the laptop as an dhcp? What ip would I ssh to if not? Do I have to ssh to a specific ip if there is only a single cable? It sounds like a great solution for what I need if it works...

---

### Post by StuartN on 2009-12-05
> **worldsayshi said:**
> Anyway, so what you are suggesting is to, instead of going via the router, set up a direct cable between the laptop and the server? But then I would have to configure some kind of connection between them and set up the laptop as an dhcp? What ip would I ssh to if not? Do I have to ssh to a specific ip if there is only a single cable? It sounds like a great solution for what I need if it works...

No, you are making this far too complicated. The ethernet cable is just an almost 100% reliable alternative path. You do not need to alter any settings or install anything.

You need only to ensure two things: 1) You know the server's IP address, or it's hostname (you can reference hostname.local instead of an IP address), and 2) The laptop has a different IP address from the server.

---

### Post by Snow986 on 2009-12-05
> **StuartN said:**
> No, you are making this far too complicated. The ethernet cable is just an almost 100% reliable alternative path. You do not need to alter any settings or install anything.

You need only to ensure two things: 1) You know the server's IP address, or it's hostname (you can reference hostname.local instead of an IP address), and 2) The laptop has a different IP address from the server.

You can not directly connect two computers and expect to ssh into the other without setting up the controller to give the other an IP (via DHCP etc).  

My suggestion is to see if you can see the server via the router.  If you can see it and that it is connected, there is no reason you shouldn't be able to ssh in (as long as port 22 is open on the server).  If you can't see the server then you know that the server is not getting an ip.  To troubleshoot network problems, I usually start from the simplest scenario possible and work up to see when it breaks. In this case, I would configure the router to just give out dynamic IPs to the whole network and see if the server connects.  If so then try to ssh in.  If you can't at this point then you know the problem lies with the server and will have to find a way in locally (such as a monitor or maybe more easily by taking out the hard drive and booting to it from another cpu.

---

### Post by StuartN on 2009-12-05
> **Snow986 said:**
> You can not directly connect two computers and expect to ssh into the other without setting up the controller to give the other an IP (via DHCP etc).

Of course not, but it has already obtained an IP address, otherwise the OP would not have been able to ssh by any means.

---

### Post by worldsayshi on 2009-12-06
> **Snow986 said:**
> You can not directly connect two computers and expect to ssh into the other without setting up the controller to give the other an IP (via DHCP etc).  

My suggestion is to see if you can see the server via the router.  If you can see it and that it is connected, there is no reason you shouldn't be able to ssh in (as long as port 22 is open on the server).  If you can't see the server then you know that the server is not getting an ip.  To troubleshoot network problems, I usually start from the simplest scenario possible and work up to see when it breaks. In this case, I would configure the router to just give out dynamic IPs to the whole network and see if the server connects.  If so then try to ssh in.  If you can't at this point then you know the problem lies with the server and will have to find a way in locally (such as a monitor or maybe more easily by taking out the hard drive and booting to it from another cpu.

Great! It worked! For some reason it was enough to just remove the static ip handout from the router and then ssh to the new ip that it got handed out. Seems like something just stopped working with the static ip handout for some reason. 

Thanks for the help! Hopefully I will get the static ip to work again in some way...

---

### Post by blackened on 2009-12-06
SSH is great if the machine is kept in a physically-hard-to-access location (like a closet), or even in a room far from where you do your general computing that would make other methods impractical.

If this is not the case and the computer is in your normal workspace area, then I would instead recommend using a KVM. 

This is not meant to circumvent the learning experience that can be gained from setting up SSH and/or VNC for remote access.

---

### Post by Snow986 on 2009-12-07
> **worldsayshi said:**
> Great! It worked! For some reason it was enough to just remove the static ip handout from the router and then ssh to the new ip that it got handed out. Seems like something just stopped working with the static ip handout for some reason. 

Thanks for the help! Hopefully I will get the static ip to work again in some way...

This is not an uncommon problem with routers.  Try resetting the router and then setting up the static IP by MAC address again.  Should work.

Glad to help!

---

