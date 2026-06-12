---
title: "What are the commands to connect to network"
date: 2010-02-21
forum: General Help
---

### Post by thameera on 2010-02-21
Hello,

Is there a way to connect to the network (internet) manually using command line, instead of clicking on the network icon and selecting the network?

(My network is ppp0. Need to write a script to connect to the network several times until it is properly connected.)

Thanks!

---

### Post by spiky001 on 2010-02-21
I have googled this, is it what you are looking for

[http://phoxis.wordpress.com/2009/05/07/bsnl-broadband-connection-in-gnulinux/](http://phoxis.wordpress.com/2009/05/07/bsnl-broadband-connection-in-gnulinux/)
[http://www.yolinux.com/TUTORIALS/LinuxTutorialPPP.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialPPP.html)

---

### Post by MinimalBin on 2010-02-21
```
sudo ifconfig ppp0 up

```

---

### Post by thameera on 2010-02-22
Thanks for the answers! I tried to get through the given articles, but seems they're beyond my comprehension yet. :( Aren't there any easier commands to disconnect and connect to the network?

---

