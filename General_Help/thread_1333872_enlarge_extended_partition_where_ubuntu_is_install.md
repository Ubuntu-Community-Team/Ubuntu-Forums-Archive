---
title: "enlarge extended partition where ubuntu is installed"
date: 2009-11-21
forum: General Help
---

### Post by winchendonsprings on 2009-11-21
What I'd like to do is enlarge my extended partition when my Ubuntu is installed.

When I booted up from the live cd and opened gparted, enlarging the extended partition(the one i want to enlarge) was not an option. Even when the 175.12GiB partition was blank(unallocated).

can this be done?

[IMG]http://lh4.ggpht.com/_IW9lx8xoDpo/SwiiL6bYuBI/AAAAAAAAAbw/ihyBw4sDbys/Screenshot--dev-sda%20-%20GParted.jpg[/IMG]

---

### Post by egalvan on 2009-11-21
The most likely reason you were unable to expand that partition was because "swap" was in use
**sda6 linux-swap**.
The LiveCD will use a swap partition if found.

Boot to the LiveCD, start up gparted, 
and right-click on the swap partition,
choose the "swapoff" option.
choose "apply", then you should be able to operate on the extended partition.

Make SURE you are booting from the LiveCD,
the screenshot shows all partitions as mounted,
as if you had booted from the hard drive install...
the LiveCD does not mount anything other than swap, by default.

---

### Post by winchendonsprings on 2009-11-21
yes, the screenshot is not from the live cd boot. thanks I will try your suggestion and turn off the swap.

Is the swap size relevant to the size of the extended partition?

-----you were right. I needed to turn the swap off when using the live cd. worked perfect. thanks a lot.

---

### Post by egalvan on 2009-11-22
Glad things worked out. That's the power of Linux.

And I just noticed that your swap partition is 16GB in size...

Unless you have 16GB of RAM, and you hibernate your machine...
Unless you work on LARGE (multi-GB large) video files...
Unless you have MANY (many dozens) of apps open at once...

you don't need that large a swap.

Nothing lost except drive space, and you seem to have plenty...
so you can leave it at that.


And if you can, please mark this thread as SOLVED, to help others.

---

### Post by winchendonsprings on 2009-11-24
Yeah I was really curious about that. Im slowly getting to know this setup as I have 12gb Ram and the most strain I put on it is maybe 2 virtual machines with 4gb each running along with some medium consumption desktop programs.

What do you think is the safest minimum I can cut the swap down to? The 16gb its using now is the default from installation.

---

