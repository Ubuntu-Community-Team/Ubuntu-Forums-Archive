---
title: "nbd and squashfs errors using LTSP"
date: 2009-07-30
forum: General Help
---

### Post by mightyiam on 2009-07-30
Dear friends,

I'm having this error in jaunty in dmesg:

[ 41.964840] nbd0: NBD_DISCONNECT
[ 41.966252] nbd0: Receive control failed (result -32)
[ 41.966552] nbd0: queue cleared
[ 41.997293] nbd0: Attempted send on closed socket
[ 41.997440] end_request: I/O error, dev nbd0, sector 378346
[ 42.003480] SQUASHFS error: sb_bread failed reading block 0x2e2f5
[ 42.003608] SQUASHFS error: Unable to read cache block [b8bd568:1a41]
[ 42.003921] SQUASHFS error: Unable to read inode [b8bd568:1a41]

This happens every single client boot.

The full dmesg is: [http://pastebin.com/f59984166](http://pastebin.com/f59984166)

This doesn't prevent the client from booting and starting ldm.

The problem that got me looking at the dmesg is that lts.conf options are ignored.

Many blessings.

---

### Post by pravindra.kumar on 2010-09-14
Hi,
I am also facing same errors, and trying to find solution.

---

### Post by boukeas on 2010-11-29
I have been facing this identical problem. Has anyone been able to figure out the cause, or a solution?

---

