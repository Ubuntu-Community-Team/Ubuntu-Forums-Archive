---
title: "things about a swap partition"
date: 2009-12-08
forum: General Help
---

### Post by abqhandyman on 2009-12-08
Hello,  I was pretty new with 9.04 when I decided to upgrade to 9.10.  I don't know that that matters much for the purpose of this question.

How do I determine whether I have a swap partition and whether it is activated?

Thank you for your response and cheers,

---

### Post by earthpigg on 2009-12-08
> **abqhandyman said:**
> Hello,  I was pretty new with 9.04 when I decided to upgrade to 9.10.  I don't know that that matters much for the purpose of this question.

How do I determine whether I have a swap partition and whether it is activated?

Thank you for your response and cheers,

free -m

example, with relevant part underlined:
```

[chris: ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1909         94          0         57       1670
-/+ buffers/cache:        181       1822
***_Swap:         1791          0       1791_***
[chris: ~]$ 
```

if you see a 0 in the first column, you have no active swap.

---

### Post by sgosnell on 2009-12-08
Open gparted, the partition editor.  You should see your swap partition, if it exists.  Right-click on it, and there should be a choice, either swapon or swapoff.  If the choice is swapon, click on it, and the swap partition will be enabled.  If the choice is swapoff, it is already enabled.  That's the easy way.

---

### Post by Sam on 2009-12-08
> **abqhandyman said:**
> How do I determine whether I have a swap partition and whether it is activated?

```
swapon -s
```

---

