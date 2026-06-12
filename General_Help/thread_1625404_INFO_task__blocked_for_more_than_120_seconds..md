---
title: "INFO: task * blocked for more than 120 seconds."
date: 2010-11-19
forum: General Help
---

### Post by SundaY82 on 2010-11-19
Hi,

I bought a usb card reader that I wanted to use on my server, it has Ubuntu 10.10 x64 server installed.

The problem I have is that when I try to access the card reader it freezes, USB module seems to lock up, process gets stuck, cant even kill it with -9. After this anything I try to do access USB like lsusb will stall and freeze, even if I first disconnect all usb devices, until I reboot system. lsusb work fine after fresh reboot, but as soon as I use an app to access the card reader everything locks up. I get this when checking dmesg:

```
[17880.830279] INFO: task newcs.x86_64:2372 blocked for more than 120 seconds.
[17880.830292] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[17880.830306] newcs.x86_64  D 00000001001a1895     0  2372      1 0x00000004
[17880.830313]  ffff8801d72bbad8 0000000000000086 ffff880200000000 0000000000015980
[17880.830319]  ffff8801d72bbfd8 0000000000015980 ffff8801d72bbfd8 ffff8801443f44a0
[17880.830325]  0000000000015980 0000000000015980 ffff8801d72bbfd8 0000000000015980
[17880.830331] Call Trace:
[17880.830338]  [<ffffffff8159d67f>] __mutex_lock_slowpath+0xff/0x190
[17880.830344]  [<ffffffff81036dc9>] ? default_spin_lock_flags+0x9/0x10
[17880.830350]  [<ffffffff8159d083>] mutex_lock+0x23/0x50
[17880.830354]  [<ffffffff8135e60a>] tty_port_open+0x6a/0xe0
[17880.830367]  [<ffffffffa0288cc0>] serial_open+0x40/0x80 [usbserial]
[17880.830373]  [<ffffffff8135753a>] tty_open+0x20a/0x610
[17880.830378]  [<ffffffff81156d9a>] chrdev_open+0x10a/0x200
[17880.830384]  [<ffffffff81156c90>] ? chrdev_open+0x0/0x200
[17880.830390]  [<ffffffff81151265>] __dentry_open+0xe5/0x330
[17880.830396]  [<ffffffff8125f6af>] ? security_inode_permission+0x1f/0x30
[17880.830402]  [<ffffffff811515c4>] nameidata_to_filp+0x54/0x70
[17880.830407]  [<ffffffff8115e0b8>] finish_open+0xe8/0x1d0
[17880.830413]  [<ffffffff81166926>] ? dput+0xd6/0x1a0
[17880.830417]  [<ffffffff8115f526>] do_last+0x86/0x460
[17880.830422]  [<ffffffff81161a65>] do_filp_open+0x425/0x660
[17880.830429]  [<ffffffff81120129>] ? handle_mm_fault+0x1b9/0x440
[17880.830435]  [<ffffffff8116ce4a>] ? alloc_fd+0x10a/0x150
[17880.830440]  [<ffffffff81151009>] do_sys_open+0x69/0x170
[17880.830446]  [<ffffffff81151150>] sys_open+0x20/0x30
[17880.830452]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
```

What can I do to resolve this?
The card reader is this one: [http://www.adteknik.se/english/usbphoenix.htm](http://www.adteknik.se/english/usbphoenix.htm)
I can add that the card reader work just fine under windows.

---

