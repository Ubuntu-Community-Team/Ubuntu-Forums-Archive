---
title: "SSH onto my machine, set up port forwarding, etc. HELP"
date: 2011-09-21
forum: General Help
---

### Post by test_tube_baby on 2011-09-21
Hello linux users,

I setup my ubuntu desktop with natty and installed ssh on it, and I have ssh installed on my macbook. I forwarded port 22 from my router to my desktop, and I also got myself a dnydns subdomain that points to my router. my computer is always on so my WAN IP doesn't change.

when i ssh into my desktop via a local connection (LAN) using:
```
ssh username@192.168.1.n
```
It connects fine!

but when I do:
```
ssh username@username.dyndns-home.com
```
i get the following output:

'ssh connection refused'.

Oh and I also allowed port 22 to be open to anyone via firestarter so it's not the firewall. I even tried turning the firewall off and no luck.

Anybody got any thoughts of wisdom?

Thanks!

---

### Post by Porcini M. on 2011-09-22
I've had similar behavior with a Verizon FIOS router - even though I could connect to machines in my LAN via port forwarding from outside, when I tried to connect in the same way from a machine within the LAN, it wouldn't work - the router seemed to intercept the connection. So perhaps you're getting that "connection refused" from the router.

---

### Post by patryk77 on 2011-09-22
Ditto, always had problems testing port forwarding from the same LAN.

You can either try to connect from another location, or ask a friend to connect from home.

It is also possible that your ISP would block port 22, and you might need to use another port.

---

### Post by test_tube_baby on 2011-09-22
turns out i can ssh using a port. but when i turn on firestarter (the port is opened through firestarter) it doesn't work. any ideas? i'm thinking of just remvoing firestarter but that may not be safe

---

### Post by patryk77 on 2011-09-22
> **test_tube_baby said:**
> i'm thinking of just remvoing firestarter but that may not be safe

You are behind a router? In that case, the router will have its own firewall you can use, so it's pretty safe.

If you want a firewall, I usually use [Webmin](http://glog.procrasstination.com/index.php?/archives/14-Installing-Webmin-on-Ubuntu!.html) to configure IPTables. Never used firestarter, but I like Webmin's interface.

---

### Post by agillator on 2011-09-22
The 'connection refused' response when trying to connect means that port 22, or the port being used, is closed or not being used by ssh server. But then you probably knew that much already. The fact that you can connect from the LAN indicates the problem is not your machine's firewall (firestarter) but your router. Go to its admin page on your browser and find its firewall or some list of services or some list of ports open or closed. That is probably where the problem lies. Let us know what you find.

---

### Post by haqking on 2011-09-22
> **agillator said:**
> The 'connection refused' response when trying to connect means that port 22, or the port being used, is closed or not being used by ssh server. But then you probably knew that much already. The fact that you can connect from the LAN indicates the problem is not your machine's firewall (firestarter) but your router. Go to its admin page on your browser and find its firewall or some list of services or some list of ports open or closed. That is probably where the problem lies. Let us know what you find.

Though this is correct, i would like to point out that alot of routers will not allow you to go out and come back in as it were.

Make sure your routers firewall is setup to port forward to your LAN IP of course, however if you still have issues then i would suggest attempting to connect from outside your own network, such as on a phone SSH client for example.

Alot of people have this trouble when trying to view there own web server when it inside there LAN.

cheers

---

### Post by agillator on 2011-09-22
haqking: I didn't realize that since I have never had that problem. In that case, may the fleas of TWO thousand camels infest their armpits! And a cable company customer service rep won't have a clue! S/he may not want to do this, but would it be possible for test_tube_baby to purchase a generic cable modem and then a fully operational router? I know you can do that with DSL, you don't HAVE to use the router your ISP gives (sells) you but I have never tried that with cable.

---

