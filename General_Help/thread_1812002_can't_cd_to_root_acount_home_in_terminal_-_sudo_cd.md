---
title: "can't cd to root acount /home in terminal - sudo cd /root fails"
date: 2011-07-25
forum: General Help
---

### Post by MechaMechanism on 2011-07-25
As subject line says.

---

### Post by coffeecat on 2011-07-25
**EDIT**: sorry, posted nonsense first time around.

You need to:

```
sudo su
cd /root
```

---

### Post by bodhi.zazen on 2011-07-25
> **MechaMechanism said:**
> As subject line says.

You can , but not in the way you think.

```
sudo bash -c "cd /root; ls -l"
```

---

### Post by MechaMechanism on 2011-07-25
Thanks coffeecat and bodhi.zazen.  That's just what I was looking for.

---

