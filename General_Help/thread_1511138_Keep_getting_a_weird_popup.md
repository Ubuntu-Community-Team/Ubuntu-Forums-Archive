---
title: "Keep getting a weird popup"
date: 2010-06-16
forum: General Help
---

### Post by ytuxedo002 on 2010-06-16
I think this happened after I upgraded to 10.04.  Any ideas?

---

### Post by ytuxedo002 on 2010-06-16
> **ytuxedo002 said:**
> I think this happened after I upgraded to 10.04.  Any ideas?
And it's always with different port numbers.

---

### Post by ytuxedo002 on 2010-06-16
Bump...sorry but it's really annoying.

---

### Post by ytuxedo002 on 2010-06-16
...

---

### Post by kerry_s on 2010-06-16
localhost is your machine
are you running a encrypted drive?

---

### Post by KeyserSoze93 on 2010-06-16
Try running:

```

sudo lsof -i tcp -i udp

```

When you see the popup (while it is still open.)

It'll show what services have tcp / udp connections open, which should help to see what's trying to act as a server and/or client.

---

### Post by ytuxedo002 on 2010-06-17
Here is what is shows:

COMMAND    PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
avahi-dae 1149      avahi   13u  IPv4   5169      0t0  UDP *:mdns 
avahi-dae 1149      avahi   14u  IPv4   5170      0t0  UDP *:51923 
cupsd     1329       root    6u  IPv6   5543      0t0  TCP localhost:ipp (LISTEN)
cupsd     1329       root    7u  IPv4   5544      0t0  TCP localhost:ipp (LISTEN)
dnsmasq   1798     nobody    5u  IPv4  10662      0t0  UDP *:bootps 
dnsmasq   1798     nobody    6u  IPv6  10667      0t0  TCP [fe80::c061:dfff:fe9f:9f9]:domain (LISTEN)
dnsmasq   1798     nobody    7u  IPv6  10668      0t0  UDP [fe80::c061:dfff:fe9f:9f9]:domain 
dnsmasq   1798     nobody    8u  IPv4  10731      0t0  TCP ygutierrez-laptop.local:domain (LISTEN)
dnsmasq   1798     nobody    9u  IPv4  10732      0t0  UDP ygutierrez-laptop.local:domain 
dhclient  1821       root    5w  IPv4  11849      0t0  UDP *:bootpc 
ubuntuone 1832 ygutierrez   20u  IPv4  12174      0t0  TCP ygutierrez-laptop.local:33904->ec2-174-129-193-12.compute-1.amazonaws.com:https (ESTABLISHED)
beam.smp  1995 ygutierrez   15u  IPv4  12193      0t0  TCP localhost:37642 (LISTEN)
beam.smp  1995 ygutierrez   17u  IPv4  33904      0t0  TCP localhost:37642->localhost:33167 (ESTABLISHED)
thunderbi 2019 ygutierrez   51u  IPv4  29362      0t0  TCP ygutierrez-laptop.local:45264->gy-in-f99.1e100.net:www (ESTABLISHED)
thunderbi 2019 ygutierrez   53u  IPv4  34774      0t0  TCP ygutierrez-laptop.local:33092->gx-in-f109.1e100.net:pop3s (ESTABLISHED)
ubuntuone 2230 ygutierrez   17u  IPv4  15782      0t0  TCP localhost:53274->localhost:37642 (CLOSE_WAIT)
firefox-b 2427 ygutierrez   46u  IPv4  33903      0t0  TCP localhost:33167->localhost:37642 (ESTABLISHED)
firefox-b 2427 ygutierrez   47u  IPv4  34125      0t0  TCP ygutierrez-laptop.local:57087->gy-in-f132.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   49u  IPv4  33906      0t0  TCP ygutierrez-laptop.local:49587->gx-in-f99.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   51u  IPv4  33961      0t0  TCP ygutierrez-laptop.local:35422->feijoa.canonical.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   63u  IPv4  34015      0t0  TCP ygutierrez-laptop.local:32837->gx-in-f132.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   64u  IPv4  34138      0t0  TCP ygutierrez-laptop.local:44884->nuq04s01-in-f113.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   65u  IPv4  34018      0t0  TCP ygutierrez-laptop.local:32838->gx-in-f132.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   66u  IPv4  34160      0t0  TCP ygutierrez-laptop.local:37805->gx-in-f113.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   67u  IPv4  34007      0t0  TCP ygutierrez-laptop.local:49590->gx-in-f99.1e100.net:www (ESTABLISHED)
firefox-b 2427 ygutierrez   68u  IPv4  34504      0t0  TCP ygutierrez-laptop.local:35434->feijoa.canonical.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   69u  IPv4  34505      0t0  TCP ygutierrez-laptop.local:35435->feijoa.canonical.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   70u  IPv4  34506      0t0  TCP ygutierrez-laptop.local:59707->l7.ycs.vip.a4e.yahoo.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   71u  IPv4  34507      0t0  TCP ygutierrez-laptop.local:59708->l7.ycs.vip.a4e.yahoo.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   72u  IPv4  34508      0t0  TCP ygutierrez-laptop.local:35438->feijoa.canonical.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   73u  IPv4  34509      0t0  TCP ygutierrez-laptop.local:35439->feijoa.canonical.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   74u  IPv4  34515      0t0  TCP ygutierrez-laptop.local:35440->feijoa.canonical.com:www (ESTABLISHED)
firefox-b 2427 ygutierrez   75u  IPv4  34527      0t0  TCP ygutierrez-laptop.local:37683->gx-in-f102.1e100.net:www (ESTABLISHED)

---

### Post by ytuxedo002 on 2010-06-17
Anybody ever seen this?

---

### Post by beckols on 2010-06-17
On the popup title bar it has a port number, make sure to post what that port number is along with the output of the lsof command.

---

### Post by ytuxedo002 on 2010-06-17
I did...it's always a different port number.  The output is above.

---

### Post by ytuxedo002 on 2010-06-17
> **beckols said:**
> On the popup title bar it has a port number, make sure to post what that port number is along with the output of the lsof command.
Here it is

---

### Post by beckols on 2010-06-17
Let me rephrase... I understand it's a different port number each time, but in order to determine what is using that port number, it's important to have the output of the lsof command along with the currently shown port from the dialog box.

---

### Post by beckols on 2010-06-17
So it looks like that is for Ubuntu One.  If you have an Ubuntu One account, that would be where you put those credentials.

---

### Post by ytuxedo002 on 2010-06-17
I gotcha...I sent both before your post.

---

### Post by ytuxedo002 on 2010-06-17
> **beckols said:**
> So it looks like that is for Ubuntu One.  If you have an Ubuntu One account, that would be where you put those credentials.

Yea i just saw that..but i am logged in and sycn'd up.  I don't know why it keeps asking me in firefox though.

---

### Post by beckols on 2010-06-17
I also notice that beam.smp is listening on that port.  Check out this post, it might apply to you:
[http://swiss.ubuntuforums.org/showthread.php?p=9449563](http://swiss.ubuntuforums.org/showthread.php?p=9449563)

---

### Post by jarviser on 2010-06-17
If this happens when you first open Firefox, are you sure that the home page for firefox isn't set to something irrelevant like the admin page of your router?

---

