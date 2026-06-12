---
title: "Are there Linux kernel diagnostics tools?"
date: 2011-07-30
forum: General Help
---

### Post by 3602 on 2011-07-30
When messing with fglrx (should not have), I may or may not have "injured" my 2.6.38-11. I was seeing oops lines.
I was able to boot into 2.6.38-8 and now 38-11 is booting correctly with no visible error lines. But I am afeared that the damage remains.
So are there any tools that can verify the integrity of my kernel, or do I simply mark for re-installation in Synaptic?
Or is there no lasting damage anyway?

Thank you very much.

---

### Post by idoitprone on 2011-07-30
> **3602 said:**
> When messing with fglrx (should not have), I may or may not have "injured" my 2.6.38-11. I was seeing oops lines.
I was able to boot into 2.6.38-8 and now 38-11 is booting correctly with no visible error lines. But I am afeared that the damage remains.
So are there any tools that can verify the integrity of my kernel, or do I simply mark for re-installation in Synaptic?
Or is there no lasting damage anyway?

Thank you very much.

check the kernel log in /var/log/kernel.log

You can always reinstall it throught the synaptic. 

Let me ask, does it boot to command line?
if it is a graphical interface then you are fine

If that does not work, then loggin in the bad kernel and check if the kernel module is there.
```

lsmod | grep -i fglrx
```if it returns nothing then

```
sudo modprobe fglrx
```else

if there is still a problem
get new drivers from ati

---

### Post by 3602 on 2011-07-30
Ah no no no, everything is correct. I am in Unity under 2.6.38-11 right now. And it's booting *fast*, too.
It is exactly when I was trying to get new Catalyst that I got errors. For some reason buildpkg returned a ton of errors. Now I installed an older fglrx through Jockey and all is fine.

---

