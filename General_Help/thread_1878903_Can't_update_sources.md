---
title: "Can't update sources"
date: 2011-11-10
forum: General Help
---

### Post by abtekk on 2011-11-10
I just performed another fresh install of the latest Lubuntu and I have an issue, during the install I selected to encrypt my home folder. Anyway, now when I try to run "sudo apt-get update" I get the following error:

```

root@lewis-AOD255:/home/lewis# apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```

Again, this is from a fresh install and I have checked and no synaptic process is running.

---

### Post by lotharmat on 2011-11-10
I'm wondering if Ubuntu is doing some kind of scheduled check for updates.. I'm probably wrong but It may be worth a shot!

---

### Post by abtekk on 2011-11-10
> **lotharmat said:**
> I'm wondering if Ubuntu is doing some kind of scheduled check for updates.. I'm probably wrong but It may be worth a shot!

Sorted it, had to restart it after sorting my encryption passphrase. Thanks anyway.

---

### Post by Rodney9 on 2011-11-10
Yes there were some updates this morning, leave it for a while and try again, let us know.


Lots of Knowledge, How To's, Screen-Casts etc on Lubuntu at - [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)


Rodney

---

