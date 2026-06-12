---
title: "sudo apt-get update not working?"
date: 2011-08-25
forum: General Help
---

### Post by Shvesley on 2011-08-25
------@-------Extensa-5620:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What is the problem?

---

### Post by dave01945 on 2011-08-25
is synaptic or software centre also open

if you type

```
sudo lsof /var/lib/dpkg/lock
```

that should tell you what process is using the file

---

### Post by WillemVoigt on 2011-11-07
Sorry. I accidentally replied to the wrong post.

---

### Post by raja.genupula on 2011-11-07
> **Shvesley said:**
> ------@-------Extensa-5620:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What is the problem?

sudo fuser -k -KILL /var/lib/dpkg/lock

try this . many times issued solved for me.

---

### Post by rudihawk on 2011-11-07
Logout and log back in again?

---

### Post by raja.genupula on 2011-11-08
> **rudihawk said:**
> Logout and log back in again?

Thats not going work and restart is the alternative but restarting means some what timed process so i suggest that

---

### Post by dfarrell07 on 2011-11-08
Did any of these solutions work for you OP?

---

### Post by pavi_elex on 2011-11-08
delete the file
 /var/lib/apt/lists/lock

---

### Post by Shvesley on 2011-11-08
ok

---

