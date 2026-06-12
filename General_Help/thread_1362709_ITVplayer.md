---
title: "ITVplayer"
date: 2009-12-23
forum: General Help
---

### Post by agkq62 on 2009-12-23
I have recently loaded Ubuntu 9.1 I am slowly finding my way round it but I am only reasonably computer literate. I tried the ITVplayer and just got a loading symbol and then a black page. I loaded Adobe Flash Plugin 10 and ITVplayer worked fine. I then shut down and restarted the computer and the ITVplayer was back to showing a loading symbol and then a black screen. Where have I gone wrong?
 

 Thanks.

---

### Post by mikem94590 on 2009-12-23
I'm not sure what ITVPlayer is, but from my Google search it appears to be a Flash based online video streaming service.  Because the codecs, Flash, and Java platforms are not included on the default Ubuntu install, I'd try installing "ubuntu-restricted-extras", which contain the proprietary codecs that may solve your problem.

You can do this with a simple;
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by agkq62 on 2009-12-23
Thanks for the quick reply. I have loaded your code but still the same problem. Funny it did work after loading the Flash Plugin.

Forgot to say that BBCiplayer works fine.

---

