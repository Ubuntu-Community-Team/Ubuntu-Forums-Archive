---
title: "How to find an IP address of somebody in the same network?"
date: 2010-05-08
forum: General Help
---

### Post by 0918028 on 2010-05-08
I want to know how I can investigate...
 
Q1- what IP address somebody has in the same network?

Q2-Is there any command I can use to figure that out?

---

### Post by Copernicus1234 on 2010-05-08
If you know the hostname, you can just ping it:

```
$ ping hackbox
PING hackbox (192.168.1.68) 56(84) bytes of data.
64 bytes from hackbox (192.168.1.68): icmp_seq=1 ttl=64 time=0.014 ms
```

If you have communicated with that computer with some program, his ip is most likely in your arp cache so you can run the arp command to find out the ip:

```

$ arp -a
? (192.168.1.68) at 01:02:07:c5:9f:a7 [ether] on eth0

```

You can also run a network scanner like nmap and scan all computers on the same network. If they respond to traffic, they will get detected.

```

sudo nmap 192.168.1.0/24

```

There are lots of ways, this is just off the top of my head. Hope it helps.

---

### Post by jobix on 2010-05-08
To add to what Copernicus1234 said, another way to do this would be to log in to your router (if applicable) and look at the list of connected computers.

---

### Post by Copernicus1234 on 2010-05-08
> **jobix said:**
> To add to what Copernicus1234 said, another way to do this would be to log in to your router (if applicable) and look at the list of connected computers.

What - when you have the option to run complicated commands instead? :p

---

### Post by StuartN on 2010-05-08
> **Copernicus1234 said:**
> You can also run a network scanner like nmap and scan all computers on the same network. If they respond to traffic, they will get detected.

```
sudo nmap 192.168.1.0/24
```

+1 for nmap - for instance sudo nmap -A 192.168.1.1/24 will list everything you need to know about your (bog standard) local network. sudo nmap -O is faster, and reveals a lot of information including operating system.

Be careful with the /24, which means preserve the first 24 bits of address, and vary the last 8 bits, scanning from 192.168.1.0 to 192.168.1.255.

192.168.1.1/32 would mean preserve all 32 bits. 192.168.1.1/16 would preserve the first 16 and vary the last 16 bits, scanning all addresses from 192.168.0.0 to 192.168.255.255.

---

### Post by 0918028 on 2010-05-14
[SIZE=5]Thank you all...[/SIZE]

---

### Post by mhgsys on 2010-05-14
> **Copernicus1234 said:**
> 
You can also run a network scanner like nmap and scan all computers on the same network. If they respond to traffic, they will get detected.

```

sudo nmap 192.168.1.0/24

```


Really nice; 
Using nmap right now because of you.

---

