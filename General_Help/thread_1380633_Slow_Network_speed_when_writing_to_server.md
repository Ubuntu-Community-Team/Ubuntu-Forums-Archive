---
title: "Slow Network speed when writing to server"
date: 2010-01-13
forum: General Help
---

### Post by Vric on 2010-01-13
I have just formated and did a fresh install to start all over.

I installed Ubuntu 9.1 and everything went fine but the network. The computer serve as a NAS and MediaPlayer.

When getting a file from the server, I get a speed of 40-60mb/sec, which are good for a Gigabit network.

When I try to put a file in, the speed can't pass more than 1mb/sec and often stop.

Here's the network info:

```


vric@XBMC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:a1:eb:55  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fea1:eb55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143036 errors:1209 dropped:0 overruns:0 frame:1209
          TX packets:86476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25864184 (25.8 MB)  TX bytes:1151156348 (1.1 GB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5084 (5.0 KB)  TX bytes:5084 (5.0 KB)

vric@XBMC:~$ sudo ethtool eth0 | grep -i speed
    Speed: 1000Mb/s


```I'm newbish in linux, so if anyone need more info, I would gladly supply them :)

Thanks

[B]Edit: Looks like it's a Gigabit Problem. I connected the Ubuntu box to my Linksys router which is 10/100 and everything is MUCH faster.

Now the question is, Why Ubuntu hate my Gigabit switch?[/B]

---

### Post by rnerwein on 2010-01-14
hi
i think there is no problem with your network. if the server send you a file he is knowing what he do ( i mean he know his system load). when you send a file to the server the ports are the throughput is almost limited - because to avoid a flooding the server up (like a attack).
ciao

---

### Post by Vric on 2010-01-14
Hi

Thanks for your reply.

I don't think it normal at all to take 9 hours to transfer a 4gb file to the server.

I redid a fresh install this night, (yea night cos when the install come to the apt part, it takes hours to complete!) and same thing.

Even Internet is incredibly slow. Trying to do the updates takes 3-4 hours. I changed Ubuntu mirror, but just updating the package info takes near an hour. Even Google is slow. Can'.t even get the NVidia driver in under an hour!

Over the web, I can't get anything better than 50kb/sec (and that's a peak.. 8k/sec seem to be the overall speed) and while transferring a file from my Windows Computer to Ubuntu, peak speed is 800ko/sec. My Windows computer and Mac Laptop have no problem whatsoever with the network.

The only thing that changed since my previous install, is that I have changed all my network (new house) and now on Gigabit.. Instead of being faster, Ubuntu is 10 time slower!

I really have no idea what to do. All the thread I find about this "problem" are unsolved or simply gives advice to use static IP and DNS (which I already do)

---

