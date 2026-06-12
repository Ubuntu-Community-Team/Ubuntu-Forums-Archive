---
title: "Can't format memory stick"
date: 2011-01-15
forum: General Help
---

### Post by kree8or on 2011-01-15
Hi all,
When I try to format my memory stick (using disk manager) , i get a error message saying "device busy", how can I stop the memory stick so I can format it?
Cheers in advance

---

### Post by kree8or on 2011-01-15
> **kree8or said:**
> Hi all,
When I try to format my memory stick (using disk manager) , i get a error message saying "device busy", how can I stop the memory stick so I can format it?
Cheers in advance
Got the drive stopped now but i'm getting the following error message:

> Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb1: Input/output error
 any ideas?
Kree

---

### Post by dental on 2011-01-15
Input/output error looks serious. I suggest you try several times (remove the USB stick, then plug it in and re-try). If you're getting the same issue then I think it means some of the memory chips in the USB stick are dead (or at least misbehaving). - So there's not much that can be done other than getting a new one.

To get some more idea of what's happening I suggest you fire up a terminal and execute the command dmesg. (That's safe... it just shows you messages from the kernel.) - I expect you see there a bunch of messagess telling you some blocks on sdb (or what that device is) could not be read/written. This would only corroborate the theory of broken USB stick.

If it was my device, I'd then try to format it by hand, from the terminal, as you might be able to get some more info. Or I'd try to zero it out with dd to see what happens. But - if you're not comfortable with the terminal then don't do that. If you mistype you could easily wreck your HDD (type sda instead of sdb and that's it). Also, this probably wouldn't help and you'd end up throwing the USB stick anyway.

One more thing - I've seen cases where some USB devices had trouble communicating with some USB controllers, and the devices worked ok with different controllers (and so different computers). Again, this is probably not the case, but before throwing the memory stick, you could check with a different computer.

---

### Post by cotcot on 2011-01-15
Maybe try with gparted. Gparted is in synaptic.
Unmount the memory stick before formatting.

---

### Post by efflandt on 2011-01-15
See if **sudo fdisk -l** (small L) shows anything for it and if it is roughly the correct size, even if that does not show partition info.

Also look through **dmesg | less** to see if that shows errors for it.

---

### Post by garvinrick4 on 2011-01-15
With flash drive unmounted use gparted to format.
Will not give access to format if mounted.
## Sorry just repeated post #4

---

