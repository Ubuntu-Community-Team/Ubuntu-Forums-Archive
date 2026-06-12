---
title: "Unable to lock the list directory"
date: 2010-03-21
forum: General Help
---

### Post by fastop on 2010-03-21
Everytime i run sudo apt-get update, it says:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory]

I researched this problem and run "dpkg --configure -a", tried to update again and the same came up.

Is there anything else I can do?

This is also happening on my laptop with ubuntu 9.10, at the moment i am on my iMac with ubuntu 10.04.

---

### Post by Sin@Sin-Sacrifice on 2010-03-21
You can only use one. Can not use apt-get with synaptic running or synaptic with Software Center, or Software center with apt-get. Close one and use the other.

---

### Post by fastop on 2010-03-21
Yes, i only have one open. I used to kill command to check if there wasnt any open, but there isnt. Ive restarted more than once so it cannot be there in the background.

---

### Post by howefield on 2010-03-21
Try

```
sudo rm /var/lib/apt/lists/lock
```

---

### Post by fastop on 2010-03-21
Ahh thankyou! That has worked perfectly. But one of the updates say...

Get: 4 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [1,039B]             
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                             
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB
  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]

It keeps stalling on 99%

---

### Post by howefield on 2010-03-21
Try a different server.

System > Administration > Software Sources > Ubuntu Software >

---

### Post by fastop on 2010-03-21
Just done that, picked the best server for me and it said...

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

This is what came up before. Ahh this is annoying!

---

