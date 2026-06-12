---
title: "add kernel to GRUB boot list"
date: 2012-07-01
forum: General Help
---

### Post by daziel on 2012-07-01
Ubuntu 10.04
The realtime kernel is not listed as a boot option
Synaptic Package Manager says these packages are installed;
linux-headers-rt
linux-rt-headers-2.6.31-10
linux-headers-2.6.31-10-rt
iproute

How do I get GRUB menu to display realtime kernel option?

Thanks

---

### Post by DJ_Max on 2012-07-01
You have to install the image, you just have the headers.

---

### Post by daziel on 2012-07-01
Can I build realtime image during installation?
I could just reinstall.

---

### Post by DJ_Max on 2012-07-01
There is no need for a re-install, just install the kernel image from the repo's

---

### Post by daziel on 2012-07-04
Got it
problem solved
Thanks

---

