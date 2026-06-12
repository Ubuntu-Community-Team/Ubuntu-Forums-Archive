---
title: "I broke /etc/interfaces"
date: 2009-07-29
forum: General Help
---

### Post by nikon_62 on 2009-07-29
I just installed Jaunty and I'm having a problem which I have made worse by trying to fix it. The original problem was that if my wired eth0 connection was set to DHCP I could access web servers on my LAN. If I set a manual address Firefox would try to add www. .com to everything for some reason. 

So for example trying to get to my network monitoring service by going to [http://mrtg](http://mrtg) would end up at [www.mrtg.com](www.mrtg.com). 

So then I got stupid and decided to hard set my static IP options in /etc/network/interfaces. Except I did that and now my connection manager says everything works fine but I can't get to any websites on the lan or web. Being a brilliant guy I forgot to back up the file before I made changes so I don't even know what to put back in the file. 

Right now there is nothing in the interfaces file. I would appreciate any help I can get.

---

### Post by hwttdz on 2009-07-29
Don't know if this will help, but I think this is the default:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

---

### Post by nikon_62 on 2009-07-29
> **hwttdz said:**
> Don't know if this will help, but I think this is the default:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

Hey thanks that was a big help. Ok I got my interfaces file back to the default and I got DHCP working again through the connection manager. I still can't set a static address and get to web servers on my LAN though. Firefox still throws www. .com onto everything like it's not even trying to get DNS from my loacl DNS server.

---

### Post by Jago6060 on 2009-07-29
> **nikon_62 said:**
> Hey thanks that was a big help. Ok I got my interfaces file back to the default and I got DHCP working again through the connection manager. I still can't set a static address and get to web servers on my LAN though. Firefox still throws www. .com onto everything like it's not even trying to get DNS from my loacl DNS server.

Sounds to me like a firefox issue(the www. .com).  It almost sounds like you have some sort of an auto complete plugin installed.  Check under your list of running plugins for firefox and see whats there.

---

### Post by asmoore82 on 2009-07-29
the `dig` command in a terminal may lend a clue to what's going on ...
```
dig mrtg
```

maybe you could add those LAN services to your hosts file,
just remember that on modern desktops you have to do it through
the NetworkManager frontend and for each network profile.

---

### Post by nikon_62 on 2009-07-30
> **asmoore82 said:**
> the `dig` command in a terminal may lend a clue to what's going on ...
```
dig mrtg
```

maybe you could add those LAN services to your hosts file,
just remember that on modern desktops you have to do it through
the NetworkManager frontend and for each network profile.


I ran dig on //calendar which is my company home page. I see it up and running in the cubicle next to me so I know it works. When I type //calendar in firefox I get redirected to [http://redirect.hotkeys.com/?a=CALENDAR.COM](http://redirect.hotkeys.com/?a=CALENDAR.COM)

```
brad@brad-laptop:~$ dig //calendar

; <<>> DiG 9.5.1-P2 <<>> //calendar
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 24709
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;//calendar.			IN	A

;; Query time: 2 msec
;; SERVER: 10.21.0.250#53(10.21.0.250)
;; WHEN: Thu Jul 30 08:29:47 2009
;; MSG SIZE  rcvd: 28

```

---

### Post by nikon_62 on 2009-07-30
Here is an update I'm not sure if this is useful info or not. I went into Firefox to edit /preferences/security tab and turned on the option for

warn me if a site tries to redirect me

Now if I put in a site name without http:// I get redirected to file:// instead of auto searching for a www. .com redirector. 

So now if I try //calendar I get file:////calendar but if I try [http://calendar](http://calendar) I still get sent to that outside website instead of my intra net site.

---

### Post by asmoore82 on 2009-07-30
Aha! that DNS server 10.21.0.250 does not have an answer for calendar ...

A valid answer would look like this:
```
**$ dig google.com**

; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48993
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

[B][COLOR="Red"];; ANSWER SECTION:
google.com.		198	IN	A	74.125.67.100
google.com.		198	IN	A	74.125.127.100
google.com.		198	IN	A	74.125.45.100[/COLOR][/B]

;; Query time: 0 msec
;; SERVER: 10.200.1.248#53(10.200.1.248)
;; WHEN: Thu Jul 30 09:07:37 2009
;; MSG SIZE  rcvd: 76
```

you could try manually appending the default search domain to the name, see
```
cat /etc/resolv.conf
```

Unless you admin the DNS box yourself, it looks like
editing your hosts file is going to be your best bet;
it seems as though NetowrkManager has backed off of it again
and you can simply edit it directly:
```
gksudo gedit /etc/hosts
```

---

### Post by nikon_62 on 2009-07-30
> **asmoore82 said:**
> Aha! that DNS server 10.21.0.250 does not have an answer for calendar ...

A valid answer would look like this:
```
**$ dig google.com**

; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48993
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

[B][COLOR="Red"];; ANSWER SECTION:
google.com.		198	IN	A	74.125.67.100
google.com.		198	IN	A	74.125.127.100
google.com.		198	IN	A	74.125.45.100[/COLOR][/B]

;; Query time: 0 msec
;; SERVER: 10.200.1.248#53(10.200.1.248)
;; WHEN: Thu Jul 30 09:07:37 2009
;; MSG SIZE  rcvd: 76
```

you could try manually appending the default search domain to the name, see
```
cat /etc/resolv.conf
```

Unless you admin the DNS box yourself, it looks like
editing your hosts file is going to be your best bet;
it seems as though NetowrkManager has backed off of it again
and you can simply edit it directly:
```
gksudo gedit /etc/hosts
```




Ok here is my hosts file. I'm not sure what exactly to put into it though.
I'm trying to wrap my head around this problem. If I use DHCP I have no issue. If I connect to our wireless in the office no problem at all. Both of those point back at 10.21.0.250 for DNS. If I manually enter an IP address and that same IP for DNS I have this problem. 

I don't mind if If I have to enter my hosts information once I figure out how. I just don't understand how the problem resolves it's self if I'm using DHCP but not manually entering the same IP info.

```
127.0.0.1	localhost
127.0.1.1	brad-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by asmoore82 on 2009-07-30
> **nikon_62 said:**
> Ok here is my hosts file. I'm not sure what exactly to put into it though.
I'm trying to wrap my head around this problem. If I use DHCP I have no issue. If I connect to our wireless in the office no problem at all. Both of those point back at 10.21.0.250 for DNS. If I manually enter an IP address and that same IP for DNS I have this problem. 

I don't mind if If I have to enter my hosts information once I figure out how. I just don't understand how the problem resolves it's self if I'm using DHCP but not manually entering the same IP info.

This is starting to make sense now ... connect with DHCP and then check out
```
cat /etc/resolv.conf
```
there will be a line in there that says "search ..."
that info needs to be entered into the "Search Domains" box when configuring a manual IP.

---

### Post by nikon_62 on 2009-07-30
> **asmoore82 said:**
> This is starting to make sense now ... connect with DHCP and then check out
```
cat /etc/resolv.conf
```
there will be a line in there that says "search ..."
that info needs to be entered into the "Search Domains" box when configuring a manual IP.

You are correct. I had to enter my domain name as the search domain and it works. Thank you asmoore82 and everyone that helped me out. This thread is resolved and I can finally watch network traffic with MRTG!

---

