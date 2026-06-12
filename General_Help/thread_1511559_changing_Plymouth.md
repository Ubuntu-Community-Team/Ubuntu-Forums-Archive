---
title: "changing Plymouth"
date: 2010-06-17
forum: General Help
---

### Post by chudder on 2010-06-17
Hi,

I've noticed there are various plymouth themes (the booting animation sequence) on synaptic but I can't figure out how to actually my plymouth theme.  I was using Ubuntu studio theme and now I changed but I can't change the plymouth theme.  is there a plymouth manager or anything?  

thanks in advance

---

### Post by mc4man on 2010-06-17
Based on what's available. (installed). the default plymouth is set thru update-alternatives, 

```
sudo update-alternatives --config default.plymouth
```

---

### Post by chudder on 2010-06-17
thanks That works

---

### Post by dcstar on 2010-06-17
> **mc4man said:**
> Based on what's available. (installed). the default plymouth is set thru update-alternatives, 

```
sudo update-alternatives --config default.plymouth
```

And if you don't want to stuff around with arcane command line typing install the **galternatives** package.

---

### Post by mc4man on 2010-06-17
> install the galternatives package.

Very handy
Hopefully alternatives continues to be put to good use - would like to see browser plugins as alt.'s

---

### Post by Zer0Nin3r on 2010-10-18
Would someone explain to me what the 'update-alternative' is and how it works?  Been using Ubuntu for some time now and this is new to me.

---

