---
title: "Cannot detect USB disks on eeepc"
date: 2010-11-29
forum: General Help
---

### Post by sepo on 2010-11-29
A friend of mine had trouble (auto)mounting USB disks on his new eeepc. When the pen/disk was connected, nothing was happening.
Here's the solution :)

Opening System -> Administration -> Disk Utility I saw that the system has detected the usbpen (/dev/sdb1) as mounted on / .
This setting probably came from an usb installation!

Looking into the fstab file I saw that there were 3 disks:
.. /proc .... (OK)
.. swap .... (OK)
/dev/sdb1  / ext4 errors=remount-ro 0 1 (WRONG)

So I edited the 3rd row this way:
/dev/sda1  / ext4 errors=remount-ro 0 1
and when rebooted everything was working fine :)

Hope this will help someone :)

---

### Post by dcstar on 2010-11-30
> **sepo said:**
> A friend of mine had trouble (auto)mounting USB disks on his new eeepc. When the pen/disk was connected, nothing was happening.
Here's the solution :)

Opening System -> Administration -> Disk Utility I saw that the system has detected the usbpen (/dev/sdb1) as mounted on / .
This setting probably came from an usb installation!

Looking into the fstab file I saw that there were 3 disks:
.. /proc .... (OK)
.. swap .... (OK)
/dev/sdb1  / ext4 errors=remount-ro 0 1 (WRONG)

So I edited the 3rd row this way:
**/dev/sda1**  / ext4 errors=remount-ro 0 1
and when rebooted everything was working fine :)

Hope this will help someone :)

That should **not** be a /dev designation, it should be a UUID= designation for just this sort of problem.

---

### Post by sepo on 2010-11-30
I was wondering if it was correct (so..thanx for the reply :) ).

Isn't the same using UUID or /path? I know that UUID are unique and not error prone....so is not safe to assume sda1 as the main disk? (maybe booting with a usb connected..?)

Thanx to everyone will respond!

---

