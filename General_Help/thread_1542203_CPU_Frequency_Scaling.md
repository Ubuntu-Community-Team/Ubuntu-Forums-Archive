---
title: "CPU Frequency Scaling"
date: 2010-07-30
forum: General Help
---

### Post by _h_ on 2010-07-30
Is there any possible way to keep my CPU frequency scaling on PERFORMANCE mode through a reboot? Ubuntu likes to default it back to ONDEMAND all the time.

---

### Post by philinux on 2010-07-30
> **_h_ said:**
> Is there any possible way to keep my CPU frequency scaling on PERFORMANCE mode through a reboot? Ubuntu likes to default it back to ONDEMAND all the time.

Yes. One way is to edit this file.

/etc/init.d/ondemand

Line 27 replace ondemand with performance. There may be a better way to do this. Someone else may chime in.

---

### Post by _h_ on 2010-07-30
> **philinux said:**
> Yes. One way is to edit this file.

/etc/init.d/ondemand

Line 27 replace ondemand with performance. There may be a better way to do this. Someone else may chime in.

Thanks, was curious because ondemand doesn't really work all that well and usually lags my laptop some when it boosts my CPU frequency up to max.

---

### Post by 2uk_ on 2010-07-30
Thanks ^ I've been wondering this too.
EDIT : nvm I got it

---

### Post by manuelb on 2010-07-30
> **_h_ said:**
> Thanks, was curious because ondemand doesn't really work all that well and usually lags my laptop some when it boosts my CPU frequency up to max.

This is the reason i usually disable ondemand whenever i perform a new installation.
The way i do it, is to install **rcconf**:

```
sudo apt-get install rcconf
```

and then:
```
sudo rcconf
```

and deselect **ondemand** from the list. Finished!

---

### Post by philinux on 2010-07-30
> **_h_ said:**
> Thanks, was curious because ondemand doesn't really work all that well and usually lags my laptop some when it boosts my CPU frequency up to max.

Try the conservative setting out as well.

---

