---
title: "ushare eth0 down"
date: 2010-09-09
forum: General Help
---

### Post by ironic.demise on 2010-09-09
I've been wrecking my brain all day and night with this issue...

This morning I did a clean install of Ubuntu 10.04 in order to completely remove windows and free up some hdd space.

I've got most things working again very quickly...

bare in mind that as far as I know, nothing relevant has changed.

I was using ushare this morning no problem, and using the same conf file it's spitting out a 
```

eth0 is down, recheck ushare.conf
ioctl cannot assign address
```

eth0 IS up
eth0 IS connected to the xbox
UFW has rules set, and has been tried disabled
the xbox cannot access the machine (eliminating it just being a false error)
I cannot access the web interface
all of the settings match several faqs, guides and my previous setup

I've uninstalled and reinstalled ushare several times.


I feel as though I shouldn't have bothered removing the dual boot now...


so, does anybody know either
how to fix the false "eth0 is down, ioctl cannot give address"
and if nobody, how can I install fruppes. it seems very very outdated with contradicting guides and when I follow the webpage it says to run a .configure but that spits a dependency at me and doesn't allow me to make the rest work.



ANY help is appreciated, this is doing my nut in and I honestly cannot see why it's gone wrong.

thankyou for your time.

---

### Post by ironic.demise on 2010-09-09
cat /etc/ushare.conf
```
# /etc/ushare.conf

USHARE_NAME=tort

USHARE_IFACE=eth0

USHARE_PORT=49153

USHARE_TELNET_PORT=1337

USHARE_DIR=/home/samuel/Public/xbox

USHARE_OVERRIDE_ICONV_ERR=yes

USHARE_ENABLE_WEB=YES

USHARE_ENABLE_TELNET=no

USHARE_ENABLE_XBOX=YES

USHARE_ENABLE_DLNA=NO

```

ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet6 addr: fe8l::110:8eef:feef:1998/14 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51828 (51.8 KB)  TX bytes:3420 (3.4 KB)
          Interrupt:21 Base address:0xef00 

```

---

### Post by ironic.demise on 2010-09-10
Any help?

---

### Post by ironic.demise on 2010-09-10
Ok, I tried setting an IP for the card myself and it stopped giving an error but the xbox couldn't connect...?

---

### Post by ironic.demise on 2010-09-11
after another fresh install, same problem... this time from a fresh config file?

---

### Post by dhughes on 2010-09-14
Pretty much exactly the same problem I am having, this is the first time I have tried it using 10.04 although I don't get any errors when using this command:

sudo /etc/init.d/ushare start

I used to use ushare -x (x for "Xbox compliant profile")

ushare won't start on the port I select in the config file I choose the default 49200 but it uses 49201 and ignores the interface I choose and picks a different IP

 It seems simple enough, the conf file is simple to use, it's so frustrating!

 I feel your pain, if I find anything I'll let you know.

 edit: I got it working! Even with the eth0 error it still works.

 I had the wrong IP in my routers port forward section I had my Xbox IP not my computer IP and the port I had in the router port forward was not what I had in the config file.

 I did end up using **ushare -x** not that other command and a bunch of restarting of my Xbox360 and ushare.

---

### Post by ironic.demise on 2010-09-14
Yeah, that seems to be my problem.
If I assign an address to the eth0 it claims to work,
ifconfig eth0 192.168.0.12
and then ushare claims that eth0 is down, but continues with the usual prompts of what's found and streamed but the xbox won't pick it up.. I assume that the network settings are correct.

When the xbox and pc are attached to the router, There are no problems
But when I plug the xbox straight into the pc it doesn't work.

It used to work, flawlessly...
It streamed media files but more importantly it allowed the xbox to connect to xbox live (don't ask, I don't get it either).

so what I'm trying to do know is have the PC connected wireless to a router, have the xbox connect to the pc wired and be able to access the internet.

---

### Post by dhughes on 2010-09-14
> **ironic.demise said:**
> ...
But when I plug the xbox straight into the pc it doesn't work.

...

 Direct, with a crossover cable?

---

