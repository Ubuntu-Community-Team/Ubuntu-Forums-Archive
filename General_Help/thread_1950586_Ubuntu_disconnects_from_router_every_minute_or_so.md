---
title: "Ubuntu disconnects from router every minute or so"
date: 2012-04-01
forum: General Help
---

### Post by ThisIsMyOtherUsername on 2012-04-01
I am running 11.10 and am using a Dlink router and my router is currently working fine with anything else, so it is a problem with Ubuntu.

This only started happening today.

---

### Post by HiImTye on 2012-04-01
is it disconnecting from the router or from the internet? please post any related logs

---

### Post by ThisIsMyOtherUsername on 2012-04-01
I'm sorry, but I'm a bit of a noob when it comes to Ubuntu, so if you could tell me how to do that, that would be great.

---

### Post by tuxtout on 2012-04-01
This could try the steps outlined here:
[https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html)

---

### Post by dcstar on 2012-04-01
> **ThisIsMyOtherUsername said:**
> I am running 11.10 and am using a Dlink router and my router is currently working fine with anything else, so it is a problem with Ubuntu.

This only started happening today.

You should have (at least) 2 kernel versions in the Grub boot menu to choose from, boot off an older kernel and see if it still occurs.

---

### Post by HiImTye on 2012-04-01
first, determine if you are being disconnected from the wireless or the internet. a good test is to see if you have an ipv4 internet address:
```
tye@T:~$ ifconfig | grep 'inet addr'
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
```
note: 127.0.0.1 is a loopback address, meaning that it is an address for your computer to send data to itself, without sending it out to your router, used for pre-processing, filtering, etc..

---

### Post by ThisIsMyOtherUsername on 2012-04-01
> **HiImTye said:**
> first, determine if you are being disconnected from the wireless or the internet. a good test is to see if you have an ipv4 internet address:
```
tye@T:~$ ifconfig | grep 'inet addr'
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
```note: 127.0.0.1 is a loopback address, meaning that it is an address for your computer to send data to itself, without sending it out to your router, used for pre-processing, filtering, etc..

Alright, I did that and got:

```
ashton@ubuntu:~$ ifconfig | grep 'inet addr'
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0

```

---

### Post by HiImTye on 2012-04-01
ok, so youre connecting to your router, next try pinging google
```
ping www.google.com
```

---

### Post by nmyrick on 2012-04-05
I have been having the same issue for about a day, and found that the issue is with the default wireless settings of the dlink router.

Go into your manual wireless network setup menu in the dlink router and make sure that your channel width is set to 'auto 20/40Mhz'

The default dlink setting is just 20 Mhz.

I reset this setting on my dlink router, and it has been working like a charm ever since!

---

