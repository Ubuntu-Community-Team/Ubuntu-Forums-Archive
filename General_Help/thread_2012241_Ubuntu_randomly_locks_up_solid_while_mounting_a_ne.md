---
title: "Ubuntu randomly locks up solid while mounting a network Windows share"
date: 2012-06-28
forum: General Help
---

### Post by ubnewbie2 on 2012-06-28
I have been trying out 12.04 for a few days and I love it.  

However, I had a few Windows shares on my network that I wanted to mount regularly, and while setting them up, I have had Ubuntu lock up solid twice.  Nothing but a power cycle would get it going again.

It happened once when mounting one share manually from the command line, and again just now after I added a new share to fstab and issued mount -a from the command line.

Both shares are on an external drive attached to my adsl router which exposes them to the network as Windows shares.

---

### Post by ubnewbie2 on 2012-06-28
and it just did it again as it booted, maybe because I now have those shares being mounted in fstab?

---

### Post by ubnewbie2 on 2012-07-01
Can no-one help with this instability?   I have had to put noauto on the lines in fstab where three Windows shares are being mounted, just to be able to boot reliably into Ubuntu

I just had it crash while umounting a share, and it went to a black screen with some sort of dump on it (and again needed to be powered off/on to get it going)

Is there a different type of underlying software (whatever it is) that I can use instead?   For example, I am thinking of using smbnetfs, as that seems like it might be safer (using fuse - a userspace system).

---

