---
title: "SSH from outside a LAN?"
date: 2010-03-11
forum: General Help
---

### Post by muteXe on 2010-03-11
got SSH working today on 2 of my machines into my main server. how easy is it to SSH into my file server from, say, my machine at work that's obviously not on my LAN?

many thanks,

mutexe

---

### Post by lisati on 2010-03-11
Many routers these days come with port-forwarding and firewall capabilities. The ease of SSH access will depend in part on the settings currently active.

---

### Post by perspectoff on 2010-03-11
There are pretty comprehensive SSH guides at

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Remote_Access)

and 

[http://kubuntuguide.org/Karmic#Remote_Access](http://kubuntuguide.org/Karmic#Remote_Access)

I'm not exactly how or why how you would use SSH on a LAN, anyway. SSH is mostly for tunnelling through the insecure Internet.

The previous user is correct -- the sticky wicket is the router. Although you can change it, the default SSH port is port 22. The router would just have to forward port 22 to the computer that has the OpenSSH server running.

The sticky wicket is if you have multiple computers on a LAN, each wanting to run an OpenSSH server. In this situation, each OpenSSH server should be listening on a different port.

For example, OpenSSH server #1 might be listening on port 11022. Then the router would forward port 11022 to that computer. 

OpenSSH server #2 might be listening on 22022. Then the router would forward port 22022 to that computer.

(The OpenSSH settings at /etc/ssh/sshd_config are used to choose which port the OpenSSH server should listen to).

In this fashion, every computer on the LAN can have its own OpenSSH server, if you choose, which can be accessed from the WAN (Internet) through the router port-forwarding.

An expert might ask: "can't you do virtual hosts with OpenSSH?" The answer is no. Unlike Apache, which allows virtual hosts, OpenSSH does not (as far as I know) allow virtual hosts at this time.

Oh yeah, the previous reply makes an excellent point -- your firewalls must allow the chosen ports to be open!

---

### Post by pricetech on 2010-03-11
Your router should allow you to forward whichever port you are using for SSH to machine hosting it.

It goes without saying you want to use the best security you have available before opening your network to the Internet.

---

### Post by muteXe on 2010-03-12
Thanks all, lots of useful reading there.

Thanks again,

mute

---

### Post by nead on 2010-03-12
Will ssh work over internet even if the router/modem doesn't have a static IP? Or should i configure it for VPN then? Or use something like openVPN? I guess that is the case, but since i'm a newb and have seen this thread just thought i could ask...

---

### Post by 3rdalbum on 2010-03-12
> **nead said:**
> Will ssh work over internet even if the router/modem doesn't have a static IP?

Yes, but you'll need to know the current IP address of the modem. I'm pretty sure there are services around where you install a program that keeps track of your IP address, and then forwards this information to a fixed URL such as "http://mycomputer.xyz.com".

It's even pretty easy to knock up a script of your own to do this, and have it e-mail your work address or whatever.

---

### Post by nemilar on 2010-03-12
You can use dyndns to setup a free domain to point to your home network, even if if you have a dynamic IP.

There are instructions here:
[http://www.techthrob.com/2009/03/02/three-steps-to-a-free-domain-for-your-home-network/](http://www.techthrob.com/2009/03/02/three-steps-to-a-free-domain-for-your-home-network/)

---

