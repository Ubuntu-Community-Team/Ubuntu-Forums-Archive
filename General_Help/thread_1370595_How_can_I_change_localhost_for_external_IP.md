---
title: "How can I change localhost for external IP"
date: 2010-01-02
forum: General Help
---

### Post by krzycir on 2010-01-02
I have a problem with showing localhost (my website is on it) on the internet, so that everyone can see it.

 On Windows all you have to do is:
open httpd.conf change ServerName 127.0.0.1 for your own IP and it works.

On Linux there is is empty httpd.conf, and configuration file apache2.conf doesn't have any address to change.
It looks like, that I have to enter my IP somewhere or some of my settings are wrong:

first computer (vista) second computer (ubuntu 9.10), cable net provider

what I did:

-activated DMZ, in my router settings and added Host IP Address: 192.168.1.100  
-active dhcp (no changes)

_Windows side:_

in TCP/IPv4 instead of automatic ip and dns I have entered my own:

Address IP: 192.168.1.103
Mask: 255.255.255.0
Gateway: 192.168.1.1

1st DNS: 192.168.1.1
2nd DNS: empty

_Linux side:_

Installed Server with: php5, apache, mysql, php my admin
I have eddited /etc/network/interfaces file:

auto lo
iface lo inet loopback
mapping hotplug
script grep
map eth0
auto eth0
iface eth0 inet static
       address 192.168.1.102
       netmask 255.255.255.0
       network 192.168.1.0
       broadcast 192.168.1.255
       gateway 192.168.1.1

reseted

Typing my own IP into browser still doesn't show my localhost.
Internet is working on my both computers, for the most of the time...
On my friend's Debian distribution of linux, all you have to do, to make it working is just simply make those changes in  /etc/network/interfaces file (setup static ip).
What am I doing wrong?

---

### Post by Charlietje on 2010-01-02
your DMZ is forwarded to 192.168.1.100
while your webserver is on 192.168.1.102

---

### Post by louieb on 2010-01-02
Is localhost defined in /etc/hosts ?

---

### Post by krzycir on 2010-01-02
> **Charlietje said:**
> your DMZ is forwarded to 192.168.1.100
while your webserver is on 192.168.1.102

Yes there is a range of 50 ips it can handle so I am manipulating in that range it should work, also I had 100 earlier nothing changed

> **louieb said:**
> Is localhost defined in /etc/hosts ?

There are only 2 lines in my /etc/hosts.conf:

order hosts, bind
multi on

---

### Post by dcstar on 2010-01-02
> **krzycir said:**
> 
There are only 2 lines in my /etc/hosts.conf:

order hosts, bind
multi on

You were not asked about that file, read the request again.

---

### Post by krzycir on 2010-01-02
Yes my bad, there is also hosts file in etc it contains the 
127.0.0.1 localhost line indeed

---

### Post by dcstar on 2010-01-02
> **krzycir said:**
> I have a problem with showing localhost (my website is on it) on the internet, so that everyone can see it.
.........
What am I doing wrong?

You just need to forward the external IP to the **real** internal IP, "localhost" is **only** for use on the **local** machine.

---

### Post by krzycir on 2010-01-02
Ok, by doing what exactly?

---

### Post by dcstar on 2010-01-02
> **krzycir said:**
> Ok, by doing what exactly?

By searching for instructions on how to do port forwarding on your router hardware.

---

### Post by louieb on 2010-01-02
[FONT=Arial]Sorry but I am confused - what is not working? 

Or I guess I should ask What is working -anything? 

If you type localhost in your browser does the site come up? [/FONT]
> Typing my own IP into browser still doesn't show my localhost.

Whch IP your internal lan IP or the one assigned by your ISP?

---

### Post by CharlesA on 2010-01-02
Need to forward port 80 (or whatever port the services are running on) to that machines local LAN IP. No need for the DMZ.

What kind of router do you have?

---

### Post by krzycir on 2010-01-03
> **louieb said:**
> [FONT=Arial]Sorry but I am confused - what is not working? 
Or I guess I should ask What is working -anything? 
If you type localhost in your browser does the site come up? [/FONT]
Whch IP your internal lan IP or the one assigned by your ISP?

Typing localhost is showing me the right content. Index of... - file list of my web directory.
Internet is not working at the moment I type this (on the linux side, windows is ok). It was working a while ago tho...
I was typing the ISP (the one from whatsmyip.com) IP into my browser and that is what I want to get working.

> **CharlesA said:**
> Need to forward port 80 (or whatever port the services are running on) to that machines local LAN IP. No need for the DMZ.
What kind of router do you have?

I have Linksys WRT54GC

---

### Post by CharlesA on 2010-01-03
> **krzycir said:**
> Typing localhost is showing me the right content. Index of... - file list of my web directory.
Internet is not working at the moment I type this (on the linux side, windows is ok). It was working a while ago tho...
I was typing the ISP (the one from whatsmyip.com) IP into my browser and that is what I want to get working.

What you need to do is forward that port to the internal IP.

Check here: [http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm)

---

### Post by krzycir on 2010-01-03
[[IMG]http://img696.imageshack.us/img696/4711/beznazwfgvy1.jpg[/IMG]]("http://img696.imageshack.us/i/beznazwfgvy1.jpg/")


This is what I did, now in my external IP I can see the router 192.168.1.1 setup site...

Disabling dmz didn't help either.

---

### Post by Charlietje on 2010-01-03
can you give the output of ifconfig?

So we can see what is what. Because I suspect you forwarded port 80 to the router itself (192.168.1.1) and not to your linux box (i gues 192.168.1.102).


Regards

---

### Post by louieb on 2010-01-03
from your 1st post
> 
_Linux side:_
...
address 192.168.1.102
...
You need forward port 80 to your Linux computers address. 
Looks like your telling the router to port forward to the router itself

---

### Post by krzycir on 2010-01-03
Well yeah, I changed it for 102 still no changes

---

### Post by Charlietje on 2010-01-03
please output your ifconfig.

---

### Post by krzycir on 2010-01-03
[[IMG]http://img171.imageshack.us/img171/5569/screenshotia.png[/IMG]]("http://img171.imageshack.us/i/screenshotia.png/")

---

### Post by CharlesA on 2010-01-04
So you cannot access the machine from outside or you cannot access it from inside the network?

---

