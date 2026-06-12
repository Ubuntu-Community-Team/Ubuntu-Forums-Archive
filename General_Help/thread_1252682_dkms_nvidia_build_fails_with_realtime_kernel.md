---
title: "dkms nvidia build fails with realtime kernel"
date: 2009-08-29
forum: General Help
---

### Post by ToneDispenser on 2009-08-29
Hello community :)

I'm running jaunty and installed the linux image and headers for the realtime kernel. But when I boot with that kernel, the xserver doesn't find the nvidia module. After removing anything related to the realtime kernel and installing the stuff again I noticed the following:

```
Setting up linux-rt-headers-2.6.28-3 (2.6.28-3.12) ...
Setting up linux-headers-2.6.28-3-rt (2.6.28-3.12) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-3-rt 
 *  nvidia (96.43.10)...       
 nvidia (96.43.10): Installing module.
............(bad exit status: 10)
  Build failed.  Installation skipped.
```

I also tried running ```
/etc/kernel/header_postinst.d/dkms 2.6.28-3-rt
```, but got the same result. 

NOTE: Works perfectly when I boot regularly (2.6.28-15-generic), it just won't work with 2.6.28-3-rt!


Thanks for any help :popcorn:

---

### Post by ToneDispenser on 2009-09-01
anyone? :(

---

### Post by ToneDispenser on 2009-09-02
After hours of bowsing and trying I found a solution. It has already been filed as a bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/385515](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/385515)

---

### Post by viralnexxus on 2009-10-09
Thanks for solving and posting because I just ran in to this problem today.

---

