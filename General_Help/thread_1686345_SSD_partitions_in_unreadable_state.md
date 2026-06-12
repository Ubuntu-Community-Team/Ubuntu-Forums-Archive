---
title: "SSD partitions in unreadable state"
date: 2011-02-12
forum: General Help
---

### Post by Philio on 2011-02-12
Last night I installed an SSD in my netbook, as it's a brand new drive I just let Ubuntu use the default "use entire disk" install option.

This morning the laptop was "stuck" in a state where I had a black screen with a mouse pointer. The pointer moved but it was otherwise unresponsive, I switched off and on again.

Kernel couldnt boot and dropped to busybox shell.

Booted USB drive, partition won't mount, can't even run a disk check.

Tried numerous ways to access the drive, nothing worked.

I deleted the partition table and rebooted, the drive is now accessible and works normally, installing currently without problem.

Anyone know what on earth could have caused the drive to get into this kind of state and how to prevent it?

---

