---
title: "Netbeans Problem"
date: 2010-08-12
forum: General Help
---

### Post by krishnandu.sarkar on 2010-08-12
Ive installed netbeans successfully. But when I try to use it, on projects page it says /usr/local/glassfish-3.0.1/glassfish/domains/domain1/config/server.policy (permission denied)

What to do?? Please help.

---

### Post by krishnandu.sarkar on 2010-08-12
It's ok guys..!! I solved it. I changed the ownership to me recursively for all subdirectories and files.

---

### Post by vjst@vitti.in on 2010-11-07
Thanks, this was helpful.
VJST

---

### Post by dark-sun on 2011-01-31
thnx bro. 
btw, here's the terminal commands for beginners like me ;)

```
cd /usr/local
sudo chown -hR $USER glassfish-3.0.1/glassfish/domains/domain1/config/server.policy

```

---

### Post by denarced on 2011-02-16
> **dark-sun said:**
> thnx bro. 
btw, here's the terminal commands for beginners like me ;)

```
cd /usr/local
sudo chown -hR $USER glassfish-3.0.1/glassfish/domains/domain1/config/server.policy

```

Just a note for everyone, the -R option seems kind of insane since referring to a single file, but there's no harm either..

---

