---
title: "E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unava"
date: 2012-07-23
forum: General Help
---

### Post by marwa aly on 2012-07-23
when i make remove some software from ubuntu software center this massage appear  E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable) E: Unable to lock the list directory
although i'm not openany termenal and nothing use apt-get 


what can i do?????????????????/:(

---

### Post by uylug on 2012-07-23
> **marwa aly said:**
> when i make remove some software from ubuntu software center this massage appear  E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable) E: Unable to lock the list directory
although i'm not openany termenal and nothing use apt-get 


what can i do?????????????????/:(

Maybe jockey running in the background?

```
ps aux | grep "jockey"
```

---

### Post by teward on 2012-07-23
Did you use 'sudo' with the apt-get command to remove software?  That's a prerequisite to remove software.

---

### Post by uylug on 2012-07-23
> **Lord of Time said:**
> Did you use 'sudo' with the apt-get command to remove software?  That's a prerequisite to remove software.

OP mentioned he is using the Software Center (USC). I assume he should have been prompted for a password?

apt-get would return:

```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

---

