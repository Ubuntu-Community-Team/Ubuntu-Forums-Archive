---
title: "can't install ies4linux in karmic"
date: 2010-02-11
forum: General Help
---

### Post by HBSC on 2010-02-11
I've never had any use for IE, all the browsers that run natively are just fine. This is the first time I've actually needed it -- I'm applying for a job that happens to be on an IE only website. (So frustrating)

I've tried many approaches to install Internet Explorer through wine and have failed so far. 
Everything I've read seems to point towards ies4linux. I attempted this:
 ```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
 tar zxvf ies4linux-latest.tar.gz
 cd ies4linux-*
 ./ies4linux

```resulting in:
```
james@HBSC:~/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).


```So I removed wine and installed version 1.0.1, which resulted in the same error. Is this wine version too new? 

I'm open to any suggestions, even if it doesn't involve ies4linux.
I would appreciate any help, I don't own a windows key. 

Thanks in advance.

---

### Post by HBSC on 2010-02-11
Bump

---

### Post by waynefoutz on 2010-02-11
Ie4linux is something i was struggling with myself just yesterday after reinstalling Ubuntu on my laptop. I could not get it to go, it kept telling me my WINE version was too old, but it's a LOT newer than the version the installer was asking for. I got IE7 installed by using playonlinux, which is a graphical front end for WINE. It's pretty good, and it had IE7 installed in no time.

[http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")

---

### Post by HBSC on 2010-02-11
Thanks for the reply, I ended up using someone else's windows machine after all, so I don't think I will attempt the playonlinux solution... until the day that I find another IE-only website that I really need to get on :)

Cheers!

---

