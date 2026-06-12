---
title: "File Server"
date: 2012-06-12
forum: General Help
---

### Post by theoldgit on 2012-06-12
I have a very strange thing going on with my samba shares.
I have an old PC set up to be a file share with samba. Originaly I had an IDE drive but this was only 60 GB so I have now replaced it with a 300Gb SATA ready for a another 300GB drive. Since re installing Ubuntu 11.10 i can get the server to work for a short time after which it seems to disconnect. If i use the browser on the server PC the samba share re appears within a few seconds, only to stop again soon after. I have set the screen saver to never come on as I thought the server PC was going to sleep but it seems to have made no difference. I'm pretty sure that samba is not the problem as I have MiniDLNA running and that dissapears at the same time. Any ideas wher I go next?

TIA

---

### Post by theoldgit on 2012-06-13
Anything?

---

### Post by stormbind on 2012-06-13
Ubuntu and all open-source collaborations are products built on knowledge-sharing, trust and honesty. I hope nobody is offended when I suggest looking for a distro called FreeNAS.

---

### Post by theoldgit on 2012-06-13
I had considered freenas but decided to go for ubuntu because i was more familiar with it. I also thought i would do a few other things with it. I'm not even sure this is an ubuntu issue but as it may be i thought i would ask here first.

Mark

---

### Post by SeijiSensei on 2012-06-13
Sounds like the network card might be powering down when not continuously in use.

Try running a task on the server that pings your router once every thirty seconds or so.  If the router has address 192.168.1.1, then you'd run:

```
ping -i 30 -n 999999999 192.168.1.1 &
```

The ampersand puts the job into the background.  The -i parameter tells it to ping every thirty seconds, and the large -n parameter means it will repeat this task 999999999 times.

---

### Post by theoldgit on 2012-06-14
I tried pinging it and that was fine. I got a response of ~3mS and never any packets lost. I shut the pc down and got some errors on that and would not shut down. Tried running the samba setup gui (forget its name) and it would not open at all. The more I did, the more errors I got. In frustration I put an old IDE drive back in (60 GIG) used that for the operating system and put one of the 300 GIG hard drives for data (the other to follow when I have time). Re installed everything and it all works like a charm. Thanks for your help but I think the install went very wrong.

Mark

---

