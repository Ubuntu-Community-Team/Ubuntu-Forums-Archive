---
title: "owner ?!"
date: 2011-02-27
forum: General Help
---

### Post by vahdani_d on 2011-02-27
hi
i cheng my owner /etc of root to sky(sky is my user)
by this coomand : chown -R sky /etc
now i use this command : sudo -i  and chand my user to root ubuntu send to me sudo: /etc/sudoers is owned by uid 1000, should be 0
how owner /etc back to root? 
plz help me
:confused:

---

### Post by CharlesA on 2011-02-27
You would need to boot into a recovery shell to fix it.

Reboot the machine, hold shift to get the grub menu and choose (recovery), then select root shell.

Run this:

```
chown -R root /etc
```

That should get it back to the correct owner.

---

### Post by vahdani_d on 2011-02-28
> **CharlesA said:**
> You would need to boot into a recovery shell to fix it.

Reboot the machine, hold shift to get the grub menu and choose (recovery), then select root shell.

Run this:

```
chown -R root /etc
```

That should get it back to the correct owner.

tnx,but  not access to server 
what way I can change owner to root  .(of long distance)
can I do this work remote.

---

### Post by CharlesA on 2011-02-28
> **vahdani_d said:**
> tnx,but  not access to server 
what way I can change owner to root  .(of long distance)
can I do this work remote.
If you can't get a root shell, then no.

---

