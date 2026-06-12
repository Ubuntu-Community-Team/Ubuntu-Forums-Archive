---
title: "Unable to connect to Google [Ubuntu 10.04]"
date: 2011-03-26
forum: General Help
---

### Post by lukjad on 2011-03-26
I've tested on different browsers, nothing doing. I tried Konqueror and got this error message:

>     The requested operation could not be completed

    Connection to Server Refused

    Details of the Request:

    URL: [http://google.com](http://google.com)

    Protocol: http

    Date and Time: Saturday 26 March 2011 13:24

    Additional Information: google.com: Socket operation timed out

    Description:

    The server google.com refused to allow this computer to make a connection.

I've turned off my modem and my router, restarted the browser and still get this issue. Cache has been cleared.

I'm really at a loss here.

Ping results:

```
    :~$ ping google.com

    PING google.com (74.125.226.84) 56(84) bytes of data.

    64 bytes from 74.125.226.84: icmp_req=1 ttl=58 time=17.8 ms

    64 bytes from 74.125.226.84: icmp_req=2 ttl=58 time=20.4 ms

    64 bytes from 74.125.226.84: icmp_req=3 ttl=58 time=18.4 ms

    64 bytes from 74.125.226.84: icmp_req=4 ttl=58 time=72.7 ms

    ^C64 bytes from 74.125.226.84: icmp_req=5 ttl=58 time=18.0 ms

    --- google.com ping statistics ---

    5 packets transmitted, 5 received, 0% packet loss, time 20239ms

    rtt min/avg/max/mdev = 17.889/29.515/72.700/21.612 ms


```

---

### Post by wanderingarticfox on 2011-03-26
I do not know Konqueror so can not help you there; but I am using Firefox with Ubuntu10.10 and I have not trouble with google. Try Firefox and set to your ISP's home page and from there Google. Hope this helps.

---

### Post by lukjad on 2011-03-26
Firefox just loads forever and never connects. It seems to be browser independant as I'm able to get to google fine when I'm using a proxy, just not direct access.

---

### Post by The Cog on 2011-03-26
Try the command **netstat -t** while firefox is trying to connect. It will show if firefox is trying to connect properly.

Also, what happens if you try the command **GET google.com** ?

---

### Post by newbuntuxx on 2011-03-26
1. Can you browse to any other site?

2. run: 
```
sudo ufw disable
```

3. Click on System - Administrator, do you see firestarter?

4. In terminal run:
```
wget google.com
```
This will output some text. Copy it and paste it here please.

5. 
- Close all programs and browsers
- Open terminal and run:
```
sudo tcpdump host google.com or port 80
```
- Then open your browser and browse to: [www.google.com](www.google.com)
- The terminal screen should have some text on it, copy it all and paste it in this thread

---

