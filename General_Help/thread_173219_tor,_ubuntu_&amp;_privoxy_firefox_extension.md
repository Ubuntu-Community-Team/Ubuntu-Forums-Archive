---
title: "tor, ubuntu &amp; privoxy: firefox extension"
date: 2006-05-10
forum: General Help
---

### Post by thespinesplitter on 2006-05-10
so....

I apt-get tor and I SHIFT+ALT+TAB to firefox where i proceed to CTRL+K to go look for privoxy, I install it and enable Tor with it, i check it out for a while and its just fine then i disabled tor from privoxy and bring up a shell

```
spine@dahcomp:~$ ping -c 5 www.google.com
PING www.l.google.com (64.233.179.104) 56(84) bytes of data.
64 bytes from 64.233.179.104: icmp_seq=1 ttl=234 time=115 ms
64 bytes from 64.233.179.104: icmp_seq=2 ttl=234 time=77.1 ms
64 bytes from 64.233.179.104: icmp_seq=3 ttl=234 time=80.3 ms
64 bytes from 64.233.179.104: icmp_seq=4 ttl=234 time=110 ms
64 bytes from 64.233.179.104: icmp_seq=5 ttl=234 time=80.7 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 77.110/92.931/115.535/16.704 ms

```


speakeasy speedtest reveals speeds of:

6145 kbps / 356 kbps


ive been been hesitant to uninstall tor because it hasnt bothered me yet, though i am confused about these ping results.


any help much appreciated.

---

### Post by ubuntu_demon on 2006-05-10
Try pinging while doing nothing on the internet with your browser closed. If you still get aproximately the same results it has nothing to do with tor/privoxy/firefox-extension/firefox.

It can also be a temporary speed problem with your provider.

---

### Post by j-strap2 on 2006-05-11
You mean, you access the privoxy config via the firefox browser, and toggle it to off? This will have no effect on the OS's internet access. 

You will have configured firefox to connect to privoxy rather than use the host operating system's network calls to access the internet. When you toggle privoxy off, this will only affect applications connecting to privoxy and Tor, nothing else. The ping command will do DNS lookups and so on using the host networking - it is unaware that privoxy is even running.

---

