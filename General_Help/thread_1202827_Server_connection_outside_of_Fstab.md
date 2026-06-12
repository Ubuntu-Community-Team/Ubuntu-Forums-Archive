---
title: "Server connection outside of Fstab"
date: 2009-07-02
forum: General Help
---

### Post by Warthaug on 2009-07-02
I am running ubuntu on a laptop which I use at home and work.  At work I connect to a file server via a wireless network.  I've set the file server connection  up using the fstab, but this has led to extremely slow shutdowns - I suspect because the wireless gets turned off before ubuntu disconnects from the server.

Fstab looks like this (user & password hidden):> 
//sglounge.dyndns.org/array1    /home/bryan/server    cifs
user=..., password=..., gid=bryan, uid=bryan, rw 0 0

In addition, I rarely need to be connected to that particular server at work, so its really not necessary to be connected every time I connect to the network.

I was wondering if there was a good app I could install that manages network connections - i.e. I could simply enter the network information once, and the use the app to open/close the connection when I need it.  Kinda like mac's "connect to network" feature.

Any recommendations?

Bryan

---

### Post by scrooge_74 on 2009-07-02
You could just try using the built int feature in places where it says connect to server and it will leave you with an icon on the desktop

---

### Post by KeyserSoze93 on 2009-07-03
add "noauto" at the end of the line in fstab, this will prevent if from being mounted a bootup.

when you do want to mount it, just open a term and run:

```
sudo mount /home/bryan/server
```

when you want to unmount it, run:

```
sudo umount /home/bryan/server
```

---

