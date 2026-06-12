---
title: "Is it possible to hibernate then resume on a different machine?"
date: 2012-05-05
forum: General Help
---

### Post by T. Amaral on 2012-05-05
I know this is an awkward subject, but I have my system on an external drive that I boot from on two different desktops, one at work and the other at home. For me this is a better solution than using a laptop, because I need the extra CPUs and memory the desktops have. The only limitation is that if I put the system into hibernation on one machine, it's not possible to wake it up on the other; the resume process can tell the machine is different and defaults to a normal boot. I wonder if it would be possible to do any tweaking that would render the resume process tolerant to the change in hardware and allow the resume process to complete? Thanks for any input.

---

### Post by dcstar on 2012-05-05
> **T. Amaral said:**
> I know this is an awkward subject, but I have my system on an external drive that I boot from on two different desktops, one at work and the other at home. For me this is a better solution than using a laptop, because I need the extra CPUs and memory the desktops have. The only limitation is that if I put the system into hibernation on one machine, it's not possible to wake it up on the other; the resume process can tell the machine is different and defaults to a normal boot. I wonder if it would be possible to do any tweaking that would render the resume process tolerant to the change in hardware and allow the resume process to complete? Thanks for any input.

Only using Virtualization.

---

### Post by T. Amaral on 2012-05-06
> **dcstar said:**
> Only using Virtualization.
Thanks. Actually some time ago I tried that using VirtualBox, by creating identical virtual machines on both computers and using raw disk access to my external drive. The performance seemed to remain very good. The main reason I dropped this solution is that I couldn't get the Guest Additions and Unity to work, but I'll look into it further.

---

