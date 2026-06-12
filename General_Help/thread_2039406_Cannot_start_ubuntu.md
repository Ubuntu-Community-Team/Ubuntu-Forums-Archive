---
title: "Cannot start ubuntu"
date: 2012-08-08
forum: General Help
---

### Post by Cold shadow on 2012-08-08
when my computer boots the ubuntu disc i burned, I arrive at the opening screen.

When I select 'Try unbuntu without change to your computer' I am taken to a DOS screen that says:

**Kernel panic.not syncing:VFS:Unab;e to mount root is on wn-block(0.0)**

and than it lists about 10 mores lines of code, and i can't type anything in, and hitting escape does nothing.

Also when I try to select another option from the ubuntu opening screen, I am taken to the same page.

Any ideas?

Additional information - I put my computer into sleep mode every night. This morning when I woke up and took it out of sleep mode it crashed. Now when I try to start my computer I get a corrupt profile error, exactly like this: [http://support.microsoft.com/kb/318011](http://support.microsoft.com/kb/318011)

---

### Post by Cold shadow on 2012-08-08
Please help!!!!

When I select "Try unbuntu without installing"

OR

"Install unbuntu"

The following screen comes up, and I am pretty much stuck on it.

**[     5.307765]** [B]Kernel panic.not syncing:VFS:Unable to mount root is on
 wn-block(0.0)
[     5.307813] Pid: 1.comm: swapper/0 Not tainted 3.2.0-23-generic-pae #3E
tu
[     5.307891] Call Trace:
[     5.307891]   [<c1592732>] ? printk+0x2d/0x2f
[     5.307929]   [<c1592600>] panic+0x5c/0x161
[     5.307966]   [<c187b5e>] mount_block_root+0xb9/8x14c
[     5.308020]   [<c115280c>] ?sys_mknod+0x2c/0x30
[     5.308057]   [<c1879d69>] mount_root+059/0x59/0x5f
[     5.308093]   [<c1879ebd>] prepare_namespace+014e/0192
[     5.308131]   [<c11434f5>] ? sys_access+0x25/0x30
[     5.308166]   [<c18798d2>] kernel_init+0140/0x145
[     5.308201]   [<c1879797>] ? start_kernel+0x35d/0x35d
[     5.308239]   [<c15af6be>] kernel_thread_helper+0x610x10
[/B]

---

### Post by Bucky Ball on 2012-08-08
What version are you using? Looking like 12.04. Have you tried boot repair?

Also, when you get to that screen with 'Try Ubuntu' hit F6 and you should get some options. Choose 'nomodset' and then try. Any luck? You could also try booting in via the recovery kernel and when you get to the options, drop to a terminal and issue:

```
sudo update-grub
```

---

### Post by Cold shadow on 2012-08-08
> **Bucky Ball said:**
> What version are you using? Looking like 12.04. Have you tried boot repair?

Also, when you get to that screen with 'Try Ubuntu' hit F6 and you should get some options. Choose 'nomodset' and then try. Any luck? You could also try booting in via the recovery kernel and when you get to the options, drop to a terminal and issue:

```
sudo update-grub
```

yes 12.04 trying everything you mentioned with boot disk last.

THANK YOU


EDIT - Sorry how do I boot via the recovery kernel?

---

### Post by Bucky Ball on 2012-08-08
When you start the computer, after BIOS screen, start mashing the shift key (used to be escape) and that should take you to the grub list. Recovery should be second on the list.

---

