---
title: "Port Forwarding Help"
date: 2011-12-18
forum: General Help
---

### Post by adamantasaurus on 2011-12-18
I'm using this guide to forward my ports.

[http://portforward.com/english/routers/port_forwarding/2wire/2701HG-B/default.htm](http://portforward.com/english/routers/port_forwarding/2wire/2701HG-B/default.htm)

I have a 2wire 2701HG-B router 

If I have to port forward ports 22 and 80, what do I need to put in the box? Would that be a port range or a single port?

Would I put 

22 (from) 80 (to)

or

22(from) 20(to)

make another one

80(from) 80(to)

Thanks

---

### Post by haqking on 2011-12-18
> **adamantasaurus said:**
> I'm using this guide to forward my ports.

[http://portforward.com/english/routers/port_forwarding/2wire/2701HG-B/default.htm](http://portforward.com/english/routers/port_forwarding/2wire/2701HG-B/default.htm)

I have a 2wire 2701HG-B router 

If I have to port forward ports 22 and 80, what do I need to put in the box? Would that be a port range or a single port?

Would I put 

22 (from) 80 (to)

or

22(from) 20(to)

make another one

80(from) 80(to)

Thanks

no, the range is for when a given app uses more than one port or a range of ports.

I presume you need SSH in which case app is SSH and the port is 22 to 22

HTTP is web server so port 80 under the app web server etc.

However may i suggest changing your SSH config to not use 22 as it is well known.

If you have a public facing box that you SSH into it is a better idea to change the ports on the SSH end and then forward to that port instead of default 22.

Edit: oh and by the way it tells you that in the link you posted ;-)

Cheers

---

### Post by mikewhatever on 2011-12-18
From 20 to 22 would open a range of ports, ie 20,21,22. From 22 to 22 would open just port 22, and from 80 to 80, just port 80.

---

### Post by adamantasaurus on 2011-12-18
> **haqking said:**
> no, the range is for when a given app uses more than one port or a range of ports.

I presume you need SSH in which case app is SSH and the port is 22 to 22

HTTP is web server so port 80 under the app web server etc.

However may i suggest changing your SSH config to not use 22 as it is well known.

If you have a public facing box that you SSH into it is a better idea to change the ports on the SSH end and then forward to that port instead of default 22.

Edit: oh and by the way it tells you that in the link you posted ;-)

Cheers

I don't understand what your saying 

"HTTP is web server so port 80 under the app web server etc." 

What do you mean port 80 under the app web server etc. 

What is the app web server?

What is a public facing box? 

How do I change my ssh config to not use 22?

Sorry for my lack of understanding but I just started using ubuntu at the beginning of this week. 

But thanks for the advice I really appreciate it.

---

### Post by adamantasaurus on 2011-12-18
> **haqking said:**
> no, the range is for when a given app uses more than one port or a range of ports.

I presume you need SSH in which case app is SSH and the port is 22 to 22

HTTP is web server so port 80 under the app web server etc.

However may i suggest changing your SSH config to not use 22 as it is well known.

If you have a public facing box that you SSH into it is a better idea to change the ports on the SSH end and then forward to that port instead of default 22.

Edit: oh and by the way it tells you that in the link you posted ;-)

Cheers

I don't understand what your saying 

"HTTP is web server so port 80 under the app web server etc." 

What do you mean port 80 under the app web server etc. 

What is the app web server?

What is a public facing box? 

How do I change my ssh config to not use 22?

Sorry for my lack of understanding but I just started using ubuntu at the beginning of this week. 

But thanks for the advice I really appreciate it.

---

### Post by haqking on 2011-12-18
> **adamantasaurus said:**
> I don't understand what your saying 

"HTTP is web server so port 80 under the app web server etc." 

What do you mean port 80 under the app web server etc. 

What is the app web server?

What is a public facing box? 

How do I change my ssh config to not use 22?

Sorry for my lack of understanding but I just started using ubuntu at the beginning of this week. 

But thanks for the advice I really appreciate it.

mmmmm ok.

You said you wanted port 80 open/forwarded so i presume you have a web server.

So in the app name in your router put a title which reflects this such as web server and use port 80 and forward it to your machine running port 80 web server.

you also said port 22 so that is SSH, so call the app ssh (or whatever you want to it is your naming convention) and add port 22 and forward it to your machine running ssh, presumably the same one running the web server.

public facing, meaning are you allowing this machine to connect to the outside world ? hence setting up this port forwarding ?

if you are then it means there is a possible security vulnerability in the remote access through SSH can be exploited.

You can change ports on your end with

/etc/ssh/sshd_config

you need to edit this file with something like vi/vim or nano or gedit etc and change the port entry (to a vlid port say 56478 or something similar, if you dont understand this then dont mess with it.

However if you are new it may be a bit much right now so dont worry too much, however make sure you use keys in SSH and not passwords, also enforce tight firewall rules for outbound and inbound.

---

### Post by adamantasaurus on 2011-12-18
> **haqking said:**
> mmmmm ok.

You said you wanted port 80 open/forwarded so i presume you have a web server.

So in the app name in your router put a title which reflects this such as web server and use port 80 and forward it to your machine running port 80 web server.

you also said port 22 so that is SSH, so call the app ssh (or whatever you want to it is your naming convention) and add port 22 and forward it to your machine running ssh, presumably the same one running the web server.

public facing, meaning are you allowing this machine to connect to the outside world ? hence setting up this port forwarding ?

if you are then it means there is a possible security vulnerability in the remote access through SSH can be exploited.

You can change ports on your end with

/etc/ssh/sshd_config

you need to edit this file with something like vi/vim or nano or gedit etc and change the port entry (to a vlid port say 56478 or something similar, if you dont understand this then dont mess with it.

However if you are new it may be a bit much right now so dont worry too much, however make sure you use keys in SSH and not passwords, also enforce tight firewall rules for outbound and inbound.

Ok thanks, that cleared it up for me.

I understand how to change rules in my firewall but what rule would I use to enforce tight rules for outbound and inbound.

Say for example I told my firewall to open port 22 and 80 what would I type to tighten up the security on those ports?

---

### Post by haqking on 2011-12-18
> **adamantasaurus said:**
> Ok thanks, that cleared it up for me.

I understand how to change rules in my firewall but what rule would I use to enforce tight rules for outbound and inbound.

Say for example I told my firewall to open port 22 and 80 what would I type to tighten up the security on those ports?

I think firewalls and rules were linked to in your other threads.

Anyway see here [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

the section on firewalls [https://wiki.ubuntu.com/BasicSecurity#Firewall](https://wiki.ubuntu.com/BasicSecurity#Firewall)

and how to enable and configure it using 3 different front ends [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

### Post by adamantasaurus on 2011-12-18
Ok so I opened the file 

/etc/ssh/sshd_config

it says

```

#what ports, IPs and protocols we listen for
Port 22


```

Do I change that number 22 to a different number like the one u mentioned 56478?

---

### Post by haqking on 2011-12-18
> **adamantasaurus said:**
> Ok so I opened the file 

/etc/ssh/sshd_config

it says

```

#what ports, IPs and protocols we listen for
Port 22


```

Do I change that number 22 to a different number like the one u mentioned 56478?


yes you can, however dont play with this until you understand it and ports.

I expect the port i stated is free, however dont use anything below 1024, if you are to use a custom port be aware that nothing is else is using it.

The Well Known Ports are those from 0 through 1023 and SHOULD NOT be used. Registered Ports are those from 1024 through 49151 should also be avoided too. **Dynamic and/or Private Ports are those from 49152 through 65535 and can be used**. 

after changing the port and saving the file then

```
/etc/init.d/ssh restart
```

and when connecting to it from your ssh client you need to specify that port so...

ssh [email]username@hostname.com[/email] -p <port number>

where the <port number> needs to be the port you configured like 56478 woudl be

```
ssh username@hostname.com -p 56478
```

---

