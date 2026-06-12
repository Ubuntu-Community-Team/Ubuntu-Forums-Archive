---
title: "Grub Capabilities"
date: 2010-11-26
forum: General Help
---

### Post by imwithid on 2010-11-26
Until I tried booting from an external USB hard drive on an older laptop whose BIOS does not support "Boot from USB Device", I was fine with Grub2. I prefer it to Grub Legacy, however, I'm confused by the numerous postings that conflict regarding external devices.

Can it really boot an external USB device even though the BIOS does not support it?

Has anyone else had this problem? The error I receive is:

```
error: no such device xxxxxxx-4xxx-xxxx-xxxx-xxxxxxxxxxxx.
error: hd1,1 cannot get C/H/S values.
error: you need to load the kernel first.

Press any key to continue...
```

When I run "ls" via the CLI in Grub (option c), I get:

```
GRUB> ls
(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)
```

I have an internal (P)ATA drive that is used as the boot loader, but would like to boot from an external USB hard drive with an SATA interface. The internal drive has some bad sectors and I really don't care to replace the hard drive as the cost/GB is not worth it but the laptop is still very functional in all other respects (as long as it isn't used as a portable computer).

So far it has worked on five other computers with some errors that were fixable.

Has any one been able to find a work around yet?

---

