---
title: "Problem re: creating LiveUSB and LiveCD"
date: 2012-08-15
forum: General Help
---

### Post by satimis on 2012-08-15
Hi all,


Ubuntu 12.04 desktop, 64bit


I have following ISO download on Fedora website
Fedora-17-x86_64-Live-Desktop.iso

Verified sha256sum correct

1)
Create LiveUSB by running
# dd if=/path/to/.iso of=/dev/sdb

It went throught without complaint. But the USB can't boot

2)
Ran;
Brasero Disc Burner
to burn CD, without complaint

But the LiveCD can't boot;
```

mount: wrong fs type, bad option, bad superblock on /dev/mapper/live-rw
.....
dracut Warning: Can/t mount root filesystem
Dropping to debu shell
dracyt:/# [ 239.943866] end_request: I/O error, dev sr0, sector 1319528
......

```

I burned it twice without solution.

Please help. TIA

In fact I need to install Fedora 17 on HD. Where can I find instruction/manual to evoke the ISO direct and to install on HD. I can copy the ISO on the HD

B.R.
satimis

---

