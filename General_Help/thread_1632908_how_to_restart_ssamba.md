---
title: "how to restart ssamba"
date: 2010-11-28
forum: General Help
---

### Post by kaykav on 2010-11-28
Hi,
          I have samba on ubuntu 10.10.I made some adjustments. Now how do I restart samba? There is no samba file in '/etc/init.d'.
          Also, where would I find the answer without going to the forum?    Thanks...Rich

---

### Post by sikander3786 on 2010-11-28
Added as a service ;-)

```
sudo service smbd restart
```

```
sudo service nmbd restart
```

---

