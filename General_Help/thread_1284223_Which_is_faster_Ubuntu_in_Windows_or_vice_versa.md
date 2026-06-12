---
title: "Which is faster Ubuntu in Windows or vice versa"
date: 2009-10-06
forum: General Help
---

### Post by mrwawa on 2009-10-06
Hi all,

I have just installed Ubuntu as a VM inside Windows and am wondering if Windows works faster inside Ubuntu or Ubuntu inside Windows.  As most of us, I would like to move to Ubuntu with Windows as a VM, but am wondering about anyone's experience.

Thanks a lot,

Wade

---

### Post by KeyserSoze93 on 2009-10-06
Well, it depends on the software you're using. I have only really run Windows XP inside Linux, and using Qemu, with the Kqemu module providing native access to the processor for the hosted OS.

With this setup most things seem to be pretty close to full speed.

You should try both, and see which is better (make sure you use something like kqemu, which seems to be the next best thing to CPU based virtualization, as in kvm, which my CPU doesn't support)

---

