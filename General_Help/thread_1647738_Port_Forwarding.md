---
title: "Port Forwarding"
date: 2010-12-17
forum: General Help
---

### Post by Harry2 on 2010-12-17
Hey :)

So I'm would like to set up a minecraft server, I already have all of the files I just need to do some port-forwarding (port 25565).

How do I do this on ubuntu, I have a Cisco Linksys router but i'm not particularly sure what the specific model is.

---

### Post by PhantmKllr on 2010-12-17
Go to your router configuration page. Open up your web browser and go to either:

192.168.0.1

or

192.168.1.1

---

### Post by Torombolo on 2010-12-17
portforward.com

You can find the model in the front of the router or in the bottom, maybe in the back also.

---

### Post by Harry2 on 2010-12-19
I've held the reset button down for 10, 30 and 60 seconds. It doesn't reset it :/

(WRT120N is the model)

---

### Post by sefs on 2010-12-19
You should not have to reset anything to port forward, did you follow the guide mentioned above?

[http://portforward.com/english/routers/port_forwarding/Linksys/WRT120N/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT120N/default.htm)

---

### Post by Harry2 on 2010-12-21
I can't login to the web interface, as (Usr: [blank] and Pwd: admin) does not work.

> harry@harry-desktop:~$ route -n | awk '/UG/ {printf "%-21s %s\n",$2,$8}'
192.168.1.1           eth2


And yes, I am trying on 192.168.1.1 with those login details.

---

### Post by Verbeck on 2010-12-21
> **Harry2 said:**
> (Usr: [blank] and Pwd: admin) does not work.

try usr:admin pass:admin

---

### Post by Harry2 on 2010-12-21
I've tried;

admin
admin

admin
[blank]

[blank]
admin

[blank]
password

[blank]
[blank]

admin
password

---

### Post by claracc on 2010-12-21
You can try, user: admin, pass:1234

Anyway you can go to the web page of your router (in internet with your browser) and to look for the default pass of admin for your these kind of router

---

### Post by Verbeck on 2010-12-21
> **Harry2 said:**
> I've tried;

then it seems like someone has changed it to prevent modifications...

---

### Post by piquat on 2010-12-22
> **Harry2 said:**
> How do I do this on ubuntu, I have a Cisco Linksys router but i'm not particularly sure what the specific model is.

You buy that yourself or get it second hand?  If someone has loaded DDWRT on it it might be root:root after a fresh reset....

Also, a little searching and you'll find sites with default user/pass combos for different routers.  Might be worth a shot once you figure out the model #.

---

### Post by Harry2 on 2010-12-22
It's a WRT120N.

I don't see how anybody could have locked it or anything, as I bought it from PCWorld.

---

### Post by QLee on 2010-12-22
> **Harry2 said:**
> It's a WRT120N.
...

This really has nothing to do with Ubuntu other than it is the operating system that you are running your browser on to access the gateway/router's configuration pages.

You need to consult the documentation that came with the router and follow the directions for port forwarding. (sometimes the default password is listed on the bottom of gateway/routers for the home market, I don't know about yours)

Cisco also has a site for support, including step-by-step solutions and FAQs.

[http://homesupport.cisco.com/en-us/wireless/lbc/WRT120N](http://homesupport.cisco.com/en-us/wireless/lbc/WRT120N)

---

