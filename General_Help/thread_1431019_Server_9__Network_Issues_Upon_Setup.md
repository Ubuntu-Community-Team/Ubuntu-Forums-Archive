---
title: "Server 9:  Network Issues Upon Setup"
date: 2010-03-16
forum: General Help
---

### Post by Devious Rhesus on 2010-03-16
Howdy all!
 
I suggested using a wiki for a bunch of our old processes where I work, and was awarded a scrubby old desktop to get it up and running. Of course, they didn't bother to ask if I knew what I was doing, so now I'm naturally struggling.
 
I've nabbed a copy of Ubuntu Server 9, and have it up and running on the old Dell Optiplex GX280 in the corner. SSH is up and running, so I can use Putty to connect. Apache is running, so I can get the little dinky "It works!" page via my web browser. Good start. Problem is, when I try pinging anything on the network, I pretty much get 100% packet loss both local and external. 
 
```

wiki@ubuntu:~$ ping [www.google.com]("http://www.google.com") -c 4
PING [www.l.google.com]("http://www.l.google.com") (72.14.204.104) 56(84) bytes of data.
From 10.11.0.166 icmp_seq=1 Destination Host Unreachable
From 10.11.0.166 icmp_seq=4 Destination Host Unreachable
--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
4 packets transmitted, 0 received, +2 errors, 100% packet loss, time 3016ms
wiki@ubuntu:~$

``` 
 
On install, I input our local proxy server info as http://10.1.15.67:80", and the ping seems to resolve google's address, so I really am quite lost at what to do. 
 
```

93 packages can be updated.
52 updates are security updates.
Last login: Mon Mar 15 20:18:41 2010 from 10.1.180.95
wiki@ubuntu:~$ sudo apt-get update
[sudo] password for wiki:
0% [Connecting to 10.1.15.67 (10.1.15.67)] [Connecting to 10.1.15.67 (10.1.15.67               Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
  Could not connect to 10.1.15.67:80 (10.1.15.67), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
  Could not connect to 10.1.15.67:80 (10.1.15.67), connection timed out
 

```
 
I also tried the apt-get to get those updates Ubuntu keeps dangling in front of me, but I seem to just bounce off the proxy server...
 
 
I've been tweaking /etc/network/interfaces and /etc/resolv.conf, but with little success. Could anybody offer me any suggestions?
 
This is my first night of ever using a Linux distro, so my appologies if this is really silly. Thanks so much for reading this far! :)

---

### Post by Devious Rhesus on 2010-03-16
Is there any additional information I can provide to attempt a resolution?  Where is the information I entered on install about the proxy stored, maybe the syntax there I messed up...
 
Thanks!

---

