---
title: "Excessive memory use in 10.04"
date: 2010-05-16
forum: General Help
---

### Post by cj.surrusco on 2010-05-16
Has anybody else notice excessive memory use with the new Ubuntu release? My system is already using over 1gb right after boot, and I have no programs set to start at boot.

---

### Post by _0R10N on 2010-05-16
That isn't happening to me. You could check your startup applications and services. Maybe there's more things starting up that you actually do.

---

### Post by steveneddy on 2010-05-16
In terminal run

```
top
```

and see if there is anything running taking lots of memory or processor time.

Also open the system Monitor and click the Processes tab. This will tell you how much memory each small app is actually using.

---

### Post by cj.surrusco on 2010-05-16
I've already checked the system monitor, there isn't much going on there, only about 100-200mb total.
Oh, and by the way, I am using amd64 if that makes a difference.

---

### Post by philinux on 2010-05-16
> **cj.surrusco said:**
> Has anybody else notice excessive memory use with the new Ubuntu release? My system is already using over 1gb right after boot, and I have no programs set to start at boot.

Could be this.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by cj.surrusco on 2010-05-28
I found the cause to this and it is very odd... It was actually due to my RAM voltage. The bios defaulted the voltage to 1.5 but the RAM is supposed to run at 1.65 volts. So I overvolted it to 1.65 and it just about doubled the system use for the RAM. 

The ram uses an appropriate amount now (about 500mb) since I set the voltage back to 1.5, but I am still having problems getting it to run at full speed however. The RAM is advertised to run at 1600mhz and my mobo is advertised to run RAM at 1400mhz and 1800mhz(overclocked). However, in the bios, I am only able to clock it up to 800mhz, and whenever I clock it over 533mhz, I get a kernel panic at boot and a lot of errors in memtest86+.

Any ideas?

---

### Post by cj.surrusco on 2010-06-13
I didn't take into account that I was overclocking my cpu. So the RAM was running faster than it was set to run because of the bus speed.

---

