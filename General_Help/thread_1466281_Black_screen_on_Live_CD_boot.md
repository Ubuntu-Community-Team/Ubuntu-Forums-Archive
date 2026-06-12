---
title: "Black screen on Live CD boot"
date: 2010-04-30
forum: General Help
---

### Post by indifference on 2010-04-30
Hello,

I'm very disappointed with lucid.. I'm getting nothing but a black screen while booting the live cd. The plymouth shows the ubuntu logo and then when it tries to launch x11 it goes black. I've tried with nomodeset and other options without success. My graphics card is an intel 855gm.

Any tips?

Kind regards,

Pedro Saraiva

---

### Post by Ozymandias_117 on 2010-04-30
How long did you give it? On my older laptop it took the CD almost 35 minutes to boot >.< It stayed at a black screen for a while during that.

---

### Post by indifference on 2010-04-30
I did wait several minutes.. But the thing is that the system is totally friezed, even the "Alt-SysRq REISUB" didn't work!

---

### Post by Shakz on 2010-04-30
Had the same issue. Reburnt the disk at the slowest setting and it worked great after that. Took two coasters to make me realize that was the issue.

---

### Post by indifference on 2010-04-30
Well, I also tried to boot using a usb pen drive with the same results :(

---

### Post by indifference on 2010-05-01
I forced X to boot with vesa and it worked.. although not very good. Then I installed this kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)
and for my surprise it's now working.

But there's a problem mounting my home partition. When I run fsck.ext4 it says:

```

The size of the filesystem (from superblock) is 31262482 blocks
The physic size of the device is 25744825 blocks
Or the superblock or the partition table are corrupted!\n
Interrupt<y>? yes

```

Any tips?

Kind regards,

Pedro Saraiva

EDIT: When I reboot with the old kernel a fsck is made and it boots normaly. Booting again with the new kernel gives me again the same error..

---

