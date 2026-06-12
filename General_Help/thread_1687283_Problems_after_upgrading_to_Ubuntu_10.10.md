---
title: "Problems after upgrading to Ubuntu 10.10"
date: 2011-02-13
forum: General Help
---

### Post by marort on 2011-02-13
I have been running Ubuntu 10.04 under Windows 7 (Is this call WUBI?) without any problems for a while. My other machines only run Ubuntu (9.04 & 10.04).
I decided to give it a try to the latest Ubuntu 10.10. After going through the successful installation and then rebooting, I am getting the following error message once   I select 'Ubuntu' in the boot up menu right after the BIOS screen:

  Booting ' Ubuntu 10.10, kernel 2.6.35-25-generic'

 Filesystem type is ntfs, partition type 0x07
The current working directory ( i.e., the relative path) is /ubuntu/disks
      [Linux-bzImage, setup=0x3400, size=0x415210]
[         0.697515] Kernel panic – not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[         0.697562] Pid: 1, comm: swapper Not tainted 2.6.35-25-generic #44-Ubuntu
[         0.697603] Call Trace:
[         0.697644]    [<c05c79a1>] ? printk+0x2d/0x34
[         0.697683]    [<c05c78fa>] panic+0x5a/0xd4
[         0.697722]    [<c0819d8d>] mount_block_root+0x1d3/0x26c
[         0.697764]    [<c022534c>] ? sys_mknod+0x2c/0x30
[         0.697804]    [<c0819e7f>]  mount_root+0x59/0x5f
[         0.697844]    [<c0819fd3>]  prepare_namespace+0x14e/0x192
[         0.697886]    [<c0217d55>] ? sys_access+0x25/0x30
[         0.697925]    [<c0819467>] kernel_init+0x18e/0x19d
[         0.698002]    [<c08192d9>]  ? kernel_init+0x0/0x19d
[         0.698042]    [<c010363e>] kernel_thread_helper+0x6/0x10


Any ideas how to take care of this problem? Is this a known issue?  Thanks

---

### Post by Rubi1200 on 2011-02-13
Hi,

1. does Windows still boot normally?

2. does Ubuntu continue to boot into the desktop or does it stall at this point and not move further?

Thanks.

---

### Post by marort on 2011-02-13
I am not having any problems with Windows. As you may know, when you install Ubuntu under Windows you get a menu -to select Windows or Ubuntu- when you start your computer. After I select Ubuntu I get the error message I mentioned earlier. It never reaches the Ubuntu logo at all.

---

### Post by bcbc on 2011-02-13
> **marort said:**
> I have been running Ubuntu 10.04 under Windows 7 (Is this call WUBI?) without any problems for a while. My other machines only run Ubuntu (9.04 & 10.04).
I decided to give it a try to the latest Ubuntu 10.10. After going through the successful installation and then rebooting, I am getting the following error message once   I select 'Ubuntu' in the boot up menu right after the BIOS screen:

  Booting ' Ubuntu 10.10, kernel 2.6.35-25-generic'

 Filesystem type is ntfs, partition type 0x07
The current working directory ( i.e., the relative path) is /ubuntu/disks
      [Linux-bzImage, setup=0x3400, size=0x415210]
[         0.697515] Kernel panic – not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[         0.697562] Pid: 1, comm: swapper Not tainted 2.6.35-25-generic #44-Ubuntu
[         0.697603] Call Trace:
[         0.697644]    [<c05c79a1>] ? printk+0x2d/0x34
[         0.697683]    [<c05c78fa>] panic+0x5a/0xd4
[         0.697722]    [<c0819d8d>] mount_block_root+0x1d3/0x26c
[         0.697764]    [<c022534c>] ? sys_mknod+0x2c/0x30
[         0.697804]    [<c0819e7f>]  mount_root+0x59/0x5f
[         0.697844]    [<c0819fd3>]  prepare_namespace+0x14e/0x192
[         0.697886]    [<c0217d55>] ? sys_access+0x25/0x30
[         0.697925]    [<c0819467>] kernel_init+0x18e/0x19d
[         0.698002]    [<c08192d9>]  ? kernel_init+0x0/0x19d
[         0.698042]    [<c010363e>] kernel_thread_helper+0x6/0x10


Any ideas how to take care of this problem? Is this a known issue?  Thanks

It looks like you have grub legacy e.g. initially you installed a release prior to 9.10 and then upgraded. This isn't very typical and I haven't seen any failures of this sort on the forums. (Mostly it appears grub-legacy wubi is more stable than grub2).

Have you tried hitting ESC and then selecting an older kernel?

---

### Post by marort on 2011-02-14
Yes, I hit ESC, but NOTHING happens. I found out that this has been happening in previous upgrades.

---

### Post by bcbc on 2011-02-14
> **marort said:**
> Yes, I hit ESC, but NOTHING happens. I found out that this has been happening in previous upgrades.

I mean before the kernel panic - when you first select ubuntu you see a countdown and "press ESC for more options". Does it still show you that option?

---

### Post by marort on 2011-02-16
Your absolutely right BCBC! I did not get it at first.

When I hit ESC the first time I get the first fragment. Then I hit ESC once again (after I select 'find /ubuntu/disks/boot/grub/menu.lst') and get the second fragment you see below.

==========================================
GRUB4DOS 0.4.4 2009-04-20, Memory: 639K /2975M, MenuEnd: 0x4355E      0

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt



==========================================
After pressing 'ESC', then 'ESC' againg I get:


GRUB4DOS 0.4.4 2009-04-20, Memory: 639K /2975M, MenuEnd: 0x4355E      1

Ubuntu 10.10,  kernel  2.6.35-25-generic
Ubuntu 10.10,  kernel  2.6.35-25-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-28-generic
Ubuntu 10.10,  kernel  2.6.32-28-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-27-generic
Ubuntu 10.10,  kernel  2.6.32-27-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-26-generic
Ubuntu 10.10,  kernel  2.6.32-26-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-25-generic
Ubuntu 10.10,  kernel  2.6.32-25-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-24-generic
Ubuntu 10.10,  kernel  2.6.32-24-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-23-generic
Ubuntu 10.10,  kernel  2.6.32-23-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-22-generic
Ubuntu 10.10,  kernel  2.6.32-22-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.31-21-generic
Ubuntu 10.10,  kernel  2.6.31-21-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.28-18-generic
Ubuntu 10.10,  kernel  2.6.28-18-generic (recovery mode)
Ubuntu 10.10,  memtest86+
Other operating systems:
Windows Vista (loader)
Windows Vista (loader)
Windows Vista (loader)


==========================================

Once I select 'Ubuntu 10.10,  kernel  2.6.32-28-generic' Ubuntu 10.10 comes up fine (at least as far as I can tell so far). 

But now the question is how can I avoid going through the same process every time I boot the machine?

Thank you very much!

---

### Post by bcbc on 2011-02-16
> **marort said:**
> Your absolutely right BCBC! I did not get it at first.

When I hit ESC the first time I get the first fragment. Then I hit ESC once again (after I select 'find /ubuntu/disks/boot/grub/menu.lst') and get the second fragment you see below.

==========================================
GRUB4DOS 0.4.4 2009-04-20, Memory: 639K /2975M, MenuEnd: 0x4355E      0

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt



==========================================
After pressing 'ESC', then 'ESC' againg I get:


GRUB4DOS 0.4.4 2009-04-20, Memory: 639K /2975M, MenuEnd: 0x4355E      1

Ubuntu 10.10,  kernel  2.6.35-25-generic
Ubuntu 10.10,  kernel  2.6.35-25-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-28-generic
Ubuntu 10.10,  kernel  2.6.32-28-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-27-generic
Ubuntu 10.10,  kernel  2.6.32-27-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-26-generic
Ubuntu 10.10,  kernel  2.6.32-26-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-25-generic
Ubuntu 10.10,  kernel  2.6.32-25-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-24-generic
Ubuntu 10.10,  kernel  2.6.32-24-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-23-generic
Ubuntu 10.10,  kernel  2.6.32-23-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.32-22-generic
Ubuntu 10.10,  kernel  2.6.32-22-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.31-21-generic
Ubuntu 10.10,  kernel  2.6.31-21-generic (recovery mode)
Ubuntu 10.10,  kernel  2.6.28-18-generic
Ubuntu 10.10,  kernel  2.6.28-18-generic (recovery mode)
Ubuntu 10.10,  memtest86+
Other operating systems:
Windows Vista (loader)
Windows Vista (loader)
Windows Vista (loader)


==========================================

Once I select 'Ubuntu 10.10,  kernel  2.6.32-28-generic' Ubuntu 10.10 comes up fine (at least as far as I can tell so far). 

But now the question is how can I avoid going through the same process every time I boot the machine?

Thank you very much!

Well you're booting your 10.04 kernel (2.6.32...). So the 10.10 kernel probably didn't get installed properly. Maybe it's just the postinst part that generates the initial ram disk.
You can try the following to recreate the initrd.img-2.6.35-25-generic:
```
sudo update-initramfs -k 2.6.35-25-generic -c
```

---

