---
title: "How To Delete Ubuntu Partition?"
date: 2011-04-18
forum: General Help
---

### Post by Chriske on 2011-04-18
Hi!

I wanted to try Ubuntu 11.04 Beta and so I installed it alongside 10.04 in a separate partition on my machine.

So, it's sitting here in /dev/sda7:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           8        1313    10485760    7  HPFS/NTFS
/dev/sda3            1313       38914   302027777    5  Extended
/dev/sda5            3344       38319   280944688+  83  Linux
/dev/sda6           38320       38914     4768768   82  Linux swap / Solaris
/dev/sda7            1313        3099    14345216   83  Linux
/dev/sda8            3099        3343     1963008   82  Linux swap / Solaris


My question is how do I now remove 11.04 from my computer safely, i.e. so that 10.04 and GRUB still work as they should?

I already tried to do it and it was a minor disaster...:(

I'm sure it must be fairly straightforward, but I'm not seeing it. Thanks.

---

### Post by mike555 on 2011-04-18
Just write over it when you install another distro,   or use gparted to format it (be careful) ......... before turning computer off -also run  in terminal type ;

                            sudo update-grub

---

### Post by Chriske on 2011-04-18
Many thanks mike555.

What I did was **_delete_** it using gparted from my 10.04 installation, then I ran sudo update-grub.

I see that I should **_format_** it instead.

Yes, that worked. Many thanks again.

---

