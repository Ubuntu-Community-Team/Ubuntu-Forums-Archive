---
title: "Accessing remote desktop over internet"
date: 2009-10-15
forum: General Help
---

### Post by arekku on 2009-10-15
Hello all.

I would like to access my home PC over the internet.

As such the steps I've taken is to turn the built-in VNC server on, instruct it to accept connections for viewing and controlling and forwarding port 5900 to 5999. Allegedly I need to forward port 5900+i, where i is the display number.

I've verified that port 5900 is open through a web-based testing server ([http://www.canyouseeme.org/](http://www.canyouseeme.org/)) which reported the port as open.

When I try to connect from my home network the connection goes through. However I've so far totally failed to connect from outside the network, and none of my friends I asked to try could either.

I'm all out of ideas on how to proceed, as such I would like to ask for help.

---

### Post by P4man on 2009-10-15
You are connecting to the correct (public) IP  address?
If you are, I can only think off a mistake in the port forwarding. Double and triple check you forwarded the correct ports to the correct local IP address, and that you set the ports to TCP and UDP.

You can also double check your local config by running:

```
sudo lsof -i
```

---

### Post by Commander_Keen on 2009-10-15
I would also like to stated, that I think you will need to do is set your PC on DMZ list on your router.

---

### Post by CharlesA on 2009-10-15
> **Commander_Keen said:**
> I would also like to stated, that I think you will need to do is set your PC on DMZ list on your router.

This wouldn't be a very good idea tbh. It means that you won't be protected by the router's firewall. You can just use port forwarding or setup a "virtual server" depending on your router so that it only forwards traffic coming from a certain port to that machine.

---

### Post by HermanAB on 2009-10-15
Hmm, and the count down to getting your machine hacked by an automated script has begun...

You should not run VNC over the internet.  It is not designed for that and there are exploits in the wild.  

You should rather use SSH, it can do everything VNC does, is much easier to set up and it is secure.

---

### Post by CharlesA on 2009-10-15
> **HermanAB said:**
> Hmm, and the count down to getting your machine hacked by an automated script has begun...

You should not run VNC over the internet.  It is not designed for that and there are exploits in the wild.  

You should rather use SSH, it can do everything VNC does, is much easier to set up and it is secure.

I Second this. I run VNC over SSH if I need to access the GUI for some reason.

---

### Post by Commander_Keen on 2009-10-15
The last thing you can do, is use Logmein.com
Its great if you want to use Ubunto to log into a Winodws PC.

---

### Post by arekku on 2009-10-15
Well I just got home and discovered my IP had changed from the one I tried to connect to.

Forwarding 5900 is sufficient to make it work.

Now on to SSL.

I'd like it to work without a user being logged in but I'll leave for after the SSL service.

Edit:
Fixed SSH tunnel.

Now on to why the screen don't update.

---

### Post by nexes128 on 2009-10-16
Since you have a dynamic public ip i would reccommed using a service like no-ip or dyndns. They offer free services (for sub domains) and update clients so if your ip changes so does the link to your ip entry in the dns.

---

