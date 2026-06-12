---
title: "Why do I get this error with curl and wget?"
date: 2009-11-02
forum: General Help
---

### Post by rob86 on 2009-11-02
I'm trying to use the commands..

```
wget theaddress -O- | tar -xv
curl theaddress | tar -xv

```
which supposedly can download and untar in one step, with no messy tarballs. 


When I use either command, I get these similar errors:

Curl:```

curl http://goodies.xfce.org/releases/notification-daemon-xfce/notification-daemon-xfce-0.3.7.tar.bz2 | tar xz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  9  321k    9 32383    0     0   1677      0  0:03:16  0:00:19  0:02:57  1935
gzip: stdin: not in gzip format
 10  321k   10 35063    0     0   1723      0  0:03:11  0:00:20  0:02:51  2257tar: Child died with signal 13
tar: Error exit delayed from previous errors
 11  321k   11 38279    0     0    796      0  0:06:53  0:00:48  0:06:05     0
```

Wget: 

```
wget http://goodies.xfce.org/releases/notification-daemon-xfce/notification-daemon-xfce-0.3.7.tar.bz2 -O- | tar xz
--2009-11-03 00:14:47--  http://goodies.xfce.org/releases/notification-daemon-xfce/notification-daemon-xfce-0.3.7.tar.bz2
Resolving goodies.xfce.org... 138.48.2.101
Connecting to goodies.xfce.org|138.48.2.101|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 329496 (322K) [application/x-tar]
Saving to: `STDOUT'

 9% [============>                                                                                                                              ] 32,862      2.26K/s  eta 2m 29s  
gzip: stdin: not in gzip format
10% [=============>                                                                                                                             ] 33,398      2.28K/s  eta 2m 29s  tar: Child died with signal 13
tar: Error exit delayed from previous errors
10% [=============>                                                                                                                             ] 33,398      2.16K/s   in 17s     


Cannot write to `-' (Broken pipe).

```



When I just normally curl or wget, the files download fine. When I try to pipe them to STDOUT for untarring, I always get the error. Why?

---

