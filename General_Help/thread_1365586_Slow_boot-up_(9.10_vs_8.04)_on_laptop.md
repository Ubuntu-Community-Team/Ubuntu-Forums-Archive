---
title: "Slow boot-up (9.10 vs 8.04) on laptop"
date: 2009-12-27
forum: General Help
---

### Post by MovingAlong on 2009-12-27
Hi all,

Wondering if anybody can help.

I've got a Sony laptop thats slightly dated technology wise (not sure of the exact spec, but would imagine 256Mb RAM).

Booting from LiveCD using 8.04 takes around 3 mins.
I've download 9.10 today hoping to make the jump, and it boots in about 11 mins or so.

Would installing to hard-disk help me at all?

I've check the disk integrity and everything seems to be good.

I do get some Buffer I/O error message when booting, with regards to device sr0.

If I can provide any further info about my set-up please let me know - or am I better sticking with version 8?

Cheers,
Greg

---

### Post by jim_charlton on 2009-12-27
sr0 is the cdrom disk.  If you see error messages about sr0 then there are probably errors on the live-CD disk.  Try burning a new CD at the lowest speed possible and check the disk afterwards for errors.

---

### Post by Sef on 2009-12-27
>  I've got a Sony laptop thats slightly dated technology wise (not sure of the exact spec, but would imagine 256Mb RAM).

Your ram is too low.  512 mb ram is really the minimum for Ubuntu.   Try [Xubuntu]("http://xubuntu.org"); it is made for older laptops.

---

### Post by emoguitarist06 on 2009-12-27
> **MovingAlong said:**
> Hi all,

Wondering if anybody can help.

I've got a Sony laptop thats slightly dated technology wise (not sure of the exact spec, but would imagine 256Mb RAM).

Booting from LiveCD using 8.04 takes around 3 mins.
I've download 9.10 today hoping to make the jump, and it boots in about 11 mins or so.

Would installing to hard-disk help me at all?

I've check the disk integrity and everything seems to be good.

I do get some Buffer I/O error message when booting, with regards to device sr0.

If I can provide any further info about my set-up please let me know - or am I better sticking with version 8?

Cheers,
Greg

Here are the minimums requirements for ubuntu
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
xubuntu would probably work better.

---

### Post by MovingAlong on 2009-12-27
Thanks for the replies.

I'll try downloading xubuntu and see how that goes.

Its a little bit of a shame because once its up it performs really well, its just that initial boot-up time.

Edit - having just run a grep "MemTotal" /proc/meminfo its returning 508820 kB - so I'm presuming I've got 512Mb.

Did a fresh burn of the disc on lower speed and did a disk integrity check - no problem again, but still get the same Buffer Read issues. I'll try and download a fresh .iso from an alternative site and retry.

Thanks again - and I'll also try Xubuntu just to see how the performance improves...

---

### Post by lukeiamyourfather on 2009-12-27
> **MovingAlong said:**
> Would installing to hard-disk help me at all?

Absolutely. As others have said Xubuntu would be a better fit for that hardware. Cheers!

---

