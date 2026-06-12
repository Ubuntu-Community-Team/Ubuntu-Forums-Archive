---
title: "How to install pyqt4"
date: 2012-02-21
forum: General Help
---

### Post by Hiuhu on 2012-02-21
Any one pliz tell me how to install pyqt4 on ubuntu 10.10

---

### Post by raja.genupula on 2012-02-21
```
sudo apt-get install python-qt4
```

type it in your terminal .

---

### Post by Hiuhu on 2012-02-23
The qt4 refused to download all it tells me is 'E: Package 'python-qt4' has no installation candidate'

---

### Post by greenpeace on 2012-02-23
Have you recently added a new repository to your system?

if yes, run: 
```
sudo apt-get update
``` 
and then:
```
sudo apt-get install python-qt4
```

---

### Post by Hiuhu on 2012-02-23
Av ran the commands and this is what is what I get:
 jemoh@Hiuhu:~$ sudo apt-get install python-qt4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-qt4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-qt4' has no installation candidate

---

### Post by greenpeace on 2012-02-23
OK... please can you post the contents of this file:

```
/etc/apt/sources.list
```

into a [pastebin]("http://pastebin.com/") and post the link here?

---

### Post by greenpeace on 2012-02-23
Just seen this: [http://ubuntuforums.org/showthread.php?t=1929032](http://ubuntuforums.org/showthread.php?t=1929032)

I suspect it is related... Did you manage to resolve that issue?

---

### Post by Hiuhu on 2012-02-23
[http://pastebin.com/y3KAs18A](http://pastebin.com/y3KAs18A)

---

### Post by Hiuhu on 2012-02-23
No I did not manage to solve it. Any suggestions ?

---

### Post by greenpeace on 2012-02-23
> **Hiuhu said:**
> No I did not manage to solve it. Any suggestions ?
I don't know what has happened to your sources, very strange.  Do you have any other connection problems from the box?  

Are you able to ping any of the addresses in the sources.list file as suggested in [that post]("http://ubuntuforums.org/showpost.php?p=11711647&postcount=6")?

```
ping -c 5 91.189.92.166
```

---

### Post by Hiuhu on 2012-02-23
When I run the 'ping' command this what I get : PING 91.189.92.166 (91.189.92.166) 56(84) bytes of data.
64 bytes from 91.189.92.166: icmp_req=1 ttl=54 time=211 ms
64 bytes from 91.189.92.166: icmp_req=2 ttl=54 time=199 ms
64 bytes from 91.189.92.166: icmp_req=3 ttl=54 time=289 ms
64 bytes from 91.189.92.166: icmp_req=4 ttl=54 time=236 ms
64 bytes from 91.189.92.166: icmp_req=5 ttl=54 time=226 ms
What could be the [problem ?

---

### Post by greenpeace on 2012-02-23
Well then you can connect to that IP.

can you post the output from ```
sudo apt-get update
```

(use pastebin again, or use code tags around it when posting)

---

### Post by Hiuhu on 2012-02-23
when I run the 'ping' command this is what I get:
jemoh@Hiuhu:~$ ping -c 5 91.189.92.166
PING 91.189.92.166 (91.189.92.166) 56(84) bytes of data.
64 bytes from 91.189.92.166: icmp_req=1 ttl=54 time=276 ms
64 bytes from 91.189.92.166: icmp_req=2 ttl=54 time=183 ms
64 bytes from 91.189.92.166: icmp_req=3 ttl=54 time=214 ms
64 bytes from 91.189.92.166: icmp_req=4 ttl=54 time=255 ms
64 bytes from 91.189.92.166: icmp_req=5 ttl=54 time=164 ms

--- 91.189.92.166 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 164.635/218.891/276.339/42.102 ms

---

### Post by Hiuhu on 2012-02-23
Ok. Here it is :
[http://pastebin.com/2CyK1kTj](http://pastebin.com/2CyK1kTj)

---

