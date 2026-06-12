---
title: "IP camera, what to do if ISP/router changes WAN IP?"
date: 2012-04-19
forum: General Help
---

### Post by qwertyjjj on 2012-04-19
I am thinking of getting a security IP camera for use outside my front door.
These connect wirelessly to the router but what happens if you do not have a fixed IP? How can you access the camera remotely?

---

### Post by 2F4U on 2012-04-19
You should make a distinction between your external IP address you get from your provider, and the internal IP addresses your devices get from your router (if it is configured as a dhcp server). Your external address may be dynamic, but your internal addresses are fixed. If you want to get access to your internal network from outside, but have a dynamic IP from your provider, there are services such as dyndns to cope with this:

[http://dyn.com/dns/](http://dyn.com/dns/)

---

### Post by jerome1232 on 2012-04-19
> **2F4U said:**
> 
[http://dyn.com/dns/](http://dyn.com/dns/)

Seconding dyndns, there is also a linux client, called ddclient, that can automatically detect a change in public ip and update your dyndns account with the change, so that the hostname is always pointing to the correct ip.

---

### Post by ingramproductions on 2012-04-19
Depending on your router model, it may also have a dynamic dns updater client on it

---

### Post by qwertyjjj on 2012-04-29
> **jerome1232 said:**
> Seconding dyndns, there is also a linux client, called ddclient, that can automatically detect a change in public ip and update your dyndns account with the change, so that the hostname is always pointing to the correct ip.

Isn't there anything free?
Also, I won't be leaving a computer on, so it would have to be linked to the router somehow with something on the firmware of the router?
Does tomato software on routers do this?

---

### Post by lisati on 2012-04-29
> **qwertyjjj said:**
> Isn't there anything free?
dyndns and no-ip both have free options
> **qwertyjjj said:**
> 
Also, I won't be leaving a computer on, so it would have to be linked to the router somehow with something on the firmware of the router?
If your security camera connects directly to your LAN, you might not need to leave your computer on.

---

### Post by qwertyjjj on 2012-05-05
> **lisati said:**
> dyndns and no-ip both have free options

If your security camera connects directly to your LAN, you might not need to leave your computer on.

But then the camera needs to support dyndns or the router needs to support it?

---

### Post by jerome1232 on 2012-05-05
> **qwertyjjj said:**
> But then the camera needs to support dyndns or the router needs to support it?

Yes, you would need something keeping the no-ip or dyndns account updated if your public ip changes. Many lynksys and netgear routers have dyndns support built right into them.

Some connections that [your public ip changing] doesn't happen a whole lot though, my public ip hasn't changed in the 8 months I've had my service.

---

### Post by lisati on 2012-05-05
> **qwertyjjj said:**
> But then the camera needs to support dyndns or the router needs to support it?

The usual method would be to get a domain name, which points to your router, which in turn passes on requests to your camera, server or other device. It probably would be easier if your router has an option to automatically update your domain registration, as the router usually takes care of the interaction between the outside world and your internal network.

---

