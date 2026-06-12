---
title: "Can anyone decipher this?"
date: 2010-12-30
forum: General Help
---

### Post by Scooter_X on 2010-12-30
I installed Lucid Netbook onto my buddy's netbook about a week ago. His HD is partitioned just as if a clean install, plus one partition for just backup when/if he has to reinstall ubuntu, because he doesn't have any external HD. 

Yesterday he texted saying it wouldn't boot up. Here's what appears when he tries to start it:

```
[            1.544638]  [<c021fd93>]  ? get_fs_type+0x33/0xb0
[            1.544713]  [<c020b65e>] ? do_kern_mount+0x3e/0xe0
[            1.544865]  [<c0222ed3>] ? do_mount+0x1c3/0x1c3/0x200
[            1.544865]  [<c0222f7b>]  ? sys_mount+0x6b/0xa0
[            1.544943]  [<c1033ec>]   ? syscall_call+0x7/0xb
[            1.545022]  [<c0590000>] ? get_kprobe+0x0/0x40
[            1.545091]  Code: 00 55 89 e5 57 89 c7 56 53 e8 a3 1f 23 00 8b 5f 04 b8 ff ff 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 4c b0 59 c0 ba
[            1.547370] EIP: [<c035b93a>]  __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f6913d6c
[            1.547370] CR2: 0000000000fc0000
[            1.547910] ---[ end trace 0dadc956d9dc130b ]---

Killed
mount: mounting/dev on /root/dev failed: No such file or directory
mount: mounting/sys on /root/sys failed: No such file or directory
mount: mounting/proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No Init Found.  Try passing= bootarg.

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Ender 'help' for a list of built-in commands.

(initramfs) _

```

And it just sits there. So I told him how to make a startup USB so he could just reinstall ubuntu fresh. He did that, tried to 'run without installing' and it just kept displaying a countdown of 5, 4, 3, 2, 1 and then would do the countdown in an infinite loop.

Currently, he's on the other side of the country with his fam for the holidays, so I can't really look at it myself until next week, but does anyone have any idea of what's going on? Or can decipher this stuff? He has an Acer AspireOne KAV60. Thanks all.

EDIT: Forgot. He also said that before it did that, it was just sitting there minding it's own business, and he came back to it eventually and it was really hot. Not to where he couldn't touch it, but he said it was still really hot. Might he have cooked his computer somehow?

---

### Post by Scooter_X on 2011-01-15
Well, not sure what happened with the first part, but the bit about the startup USB drive, I don't know what happened but I just made a new one and it worked. I wonder how he did it in the first place? Hmmm...

Anyway, just as a reference in case anyone else happens to have a related issue. I hate when I have an issue and find another issue but that never had any replies or anything.

---

