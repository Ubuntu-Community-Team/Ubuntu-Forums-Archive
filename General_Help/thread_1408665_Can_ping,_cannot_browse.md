---
title: "Can ping, cannot browse"
date: 2010-02-16
forum: General Help
---

### Post by Lockheed on 2010-02-16
I can ping IP addresses of sites, say 209.85.229.99 (google.com), but I cannot ping google.com, nor browse it.
Same thing for every alphabetic address and hence in practice I have no internet on my laptop.

In windows, I'd just flush DNS but I don't know what to do in Ubuntu. I am using WICD.

---

### Post by Sealbhach on 2010-02-16
That sounds like a problem with DNS nameservers. Try switching to [OpenDNS]([http://www.opendns.com/](http://www.opendns.com/)).

.

---

### Post by bodhi.zazen on 2010-02-16
What is in the file

/etc/resolv.conf ?

```
cat /etc/resolv.conf
```

If it is empty, open the file with an editro and add in your router IP address.

```
gksu gedit /etc/resolv.conf
```

Add in

nameserver 192.168.0.1 <---Change this IP to your router IP

---

### Post by wrightrocket on 2010-02-16
> **Lockheed said:**
> I can ping IP addresses of sites, say 209.85.229.99 (google.com), but I cannot ping google.com, nor browse it.
Same thing for every alphabetic address and hence in practice I have no internet on my laptop.

In windows, I'd just flush DNS but I don't know what to do in Ubuntu. I am using WICD.
If you are using the NetworkManager, and want to set your own DNS server: then right click the NetworkManager icon on the upper desktop panel and choose Edit Connections. Next, click the tab for the type of the connection you are using, click the name of the settings that you are using, and click the Edit button. Now, on the IPv4 tab, you can select either Manual or DHCP (Addresses Only), and you will be able to enter a comma separated list of DNS servers that you can use, such as 4.2.2.2,4.2.2.3 for example.

---

### Post by Lockheed on 2010-02-16
> **bodhi.zazen said:**
> What is in the file

/etc/resolv.conf ?

```
cat /etc/resolv.conf
```

If it is empty, open the file with an editro and add in your router IP address.

```
gksu gedit /etc/resolv.conf
```

Add in

nameserver 192.168.0.1 <---Change this IP to your router IP

Bingo.
Is there any way to make it automatic, so that I don't have to change it manually every time I connect to different network?

---

### Post by bodhi.zazen on 2010-02-16
> **wrightrocket said:**
> If you are using the NetworkManager, and want to set your own DNS server: then right click the NetworkManager icon on the upper desktop panel and choose Edit Connections. Next, click the tab for the type of the connection you are using, click the name of the settings that you are using, and click the Edit button. Now, on the IPv4 tab, you can select either Manual or DHCP (Addresses Only), and you will be able to enter a comma separated list of DNS servers that you can use, such as 4.2.2.2,4.2.2.3 for example.

> **Lockheed said:**
> I can ping IP addresses of sites, say 209.85.229.99 (google.com), but I cannot ping google.com, nor browse it.
Same thing for every alphabetic address and hence in practice I have no internet on my laptop.

In windows, I'd just flush DNS but I don't know what to do in Ubuntu. I am using WICD.

> **Lockheed said:**
> Bingo.
Is there any way to make it automatic, so that I don't have to change it manually every time I connect to different network?

You are probably fine. I do not recall the wicd menu off the top of my head, but similar to networkmanager there should be an option to set it (if needed).

---

### Post by Lockheed on 2010-02-16
I am pretty sure there is no option for this in WICD as I looked for it everywhere I could think of.

---

### Post by bodhi.zazen on 2010-02-16
I installed wicd ...

You set a DNS uner your network connection, under preferences.

---

### Post by akakingess on 2010-02-16
+1 for 4.2.2.2 and 4.2.2.3, I think those are GEs or something, but I have never had a problem with them and use them on whichever network I am on.

---

### Post by Lockheed on 2010-02-17
> **bodhi.zazen said:**
> I installed wicd ...

You set a DNS uner your network connection, under preferences.

Well, I know about setting the external DNS server addresses but I mean is it possible to set WICD to always use router's IP?

Also, in /etc/resolv.conf, is it possible to set more than one IP address?

---

### Post by rnerwein on 2010-02-17
hi
Also, in /etc/resolv.conf, is it possible to set more than one IP  address?
yes it is - just have a look at: man resolv.conf
ciao

---

### Post by Lockheed on 2010-02-17
> **rnerwein said:**
> hi
Also, in /etc/resolv.conf, is it possible to set more than one IP  address?
yes it is - just have a look at: man resolv.conf
ciao

Although very informative, it does not say how to separate ip addresses.

---

### Post by bodhi.zazen on 2010-02-17
You may have multiple Ip in /etc/resolv.conf

nameserver ip_1
nameserver ip_2

etc

When I installed wicd yesterday it automatically configured my resolv.conf

What router and network card do you have ? Try a google search to see if there are any problems with your hardware.

---

