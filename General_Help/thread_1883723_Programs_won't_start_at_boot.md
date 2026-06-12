---
title: "Programs won't start at boot"
date: 2011-11-19
forum: General Help
---

### Post by DarkGreen16 on 2011-11-19
I've done a fresh 11.10 64 bit installation and have made very little modifications to the system other than the guide mentioned here to fix the error described on [said page]("http://bradleyayers.blogspot.com/2011/10/upstart-user-jobs-on-ubuntu-1110.html")

The problem I'm having is that items in /etc/init.d are not starting with the machine. However, if I start them manually using 

```
sudo /etc/init.d/mumble-server start
```

they work just fine.

I've also tried but this doesn't work either

```
update-rc.d mumble-server defaults
```

---

