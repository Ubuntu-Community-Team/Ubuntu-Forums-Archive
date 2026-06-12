---
title: "Kernel Panic with new update"
date: 2010-03-07
forum: General Help
---

### Post by Nuskrad on 2010-03-07
A few days ago there was a new set of Ubuntu updates, I didn't examine too closely in detail what exactly all the updates were. Upon restarting, there was a new entry in the grub menu, **Ubuntu, Linux 2.6.31-20-generic**. Trying to boot this option results in the following:

[Linux-bzImage, setup=0x3400, size=0x3c01a0]
[Initrd, addr=0x3782b000, size=0x7c407a]
[     3.875982] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)

Selecting the recovery mode option results in the same, but there's a lot more detail before it.

The 2.6.31-19 option is still there and boots up fine, so there's no major issues, just wondering why it's coming up with this error and if there's a way to fix it. I'm using a Wubi install which may be what's causing it, as I understand it uses a virtual filesystem which this update might not be expecting.

---

### Post by loathsome on 2010-03-11
Hello!

I have the exact same problem. Anyone knows what causes this, and how to eventually fix it? Although it is, as Nuskrad already have stated, no major problem since 2.6.31-19 still shows up.

- edit -
I am running W7, so it is not the "exact" same problem. This probably does not matter anyway!

Thanks!

---

### Post by loathsome on 2010-03-11
I found this bug thread: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104")

Some people have reportedly fixed the problem. I will try later and report back.

---

### Post by Kdawkins on 2010-03-15
Bump... does anyone have a solution to this problem? I am having this issue also...

---

