---
title: "DNS lookup"
date: 2006-05-12
forum: General Help
---

### Post by qrees on 2006-05-12
Whenever I try to open some webpage, there is status text: "Looking up somesite.com". This process takes a lot of time (about 5 seconds). It's seems like sites IP addresses are not cached, so browser have to look for IP everytime i view the page(but I'm not an expert ;) ). Any ideas how to solve this? I've already searched forum, but i'm not sure what i have to look for. I'm using firefox.

---

### Post by cyracks on 2006-05-12
Type **about:config** in address field and you will get various options for configuring firefox.

---

### Post by qrees on 2006-05-12
But I'm not sure if this is only firefox foult. I'll try to configure something, but there are a LOT of options and some more help would be usefull.

---

### Post by cyracks on 2006-05-12
If you refresh a page, does it take long to **start** refreshing ?
How fast is you internet connection ?

To check out if you have DNS server problem do the following

```

cat /etc/resolv.conf |grep nameserver

```

You will get something like:

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

Now try to ping servers (look at ping time)

```

ping xxx.xxx.xxx.xxx

```

---

### Post by qrees on 2006-05-12
Yes, I always have to wait for "looking for....". I tried to ping these servers and it's less than 10ms everytime so this is not the problem. But when you are looking for IP of domain you have to ask that's domain namesserver, not my (I think so...). I remember that windows had somethink like hosts file, where domain and IP's where stored. Is there something similar in Ubuntu?

---

### Post by cyracks on 2006-05-12
[QUOTE=qrees]But when you are looking for IP of domain you have to ask that's domain namesserver[/QUOTE]

That is true

[QUOTE=qrees]
not my (I think so...)
[/QUOTE]

That is not true, you server asks for you.If you are looking for test.com, you  ask your server and that server ask another server and another... when request reaches server responsible for com domain it replayes from its database what is the ip number of the computer you are looking for. (unless some other server in the line have the requested address cached)

[QUOTE=qrees]
I remember that windows had somethink like hosts file, where domain and IP's where stored. Is there something similar in Ubuntu?
[/QUOTE]
/etc/hosts

This file is used only for computers which you know about (same in windows).

---

### Post by qrees on 2006-05-12
So any ideas what is wrong?

---

### Post by cyracks on 2006-05-12
[QUOTE=qrees]less than 10ms [/QUOTE]
This is quite fast, what is the ip of your DNS server ?

If you refresh a page, does it take long to start refreshing ?
How fast is you internet connection ?

---

### Post by qrees on 2006-05-12
```
nameserver 212.76.39.205
nameserver 212.76.39.211
```

---

### Post by cyracks on 2006-05-12
How long does this take

```

ping -c 1 www.google.com

```

---

### Post by qrees on 2006-05-12
```
PING www.l.google.com (66.249.93.104) 56(84) bytes of data.
64 bytes from 66.249.93.104: icmp_seq=1 ttl=240 time=45.8 ms

--- www.l.google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 45.849/45.849/45.849/0.000 ms
```

---

### Post by cyracks on 2006-05-12
Sorry, out of ideas.

---

### Post by qrees on 2006-05-13
Problem solved after installing Swiftfox, but Firefox is still slow.

---

