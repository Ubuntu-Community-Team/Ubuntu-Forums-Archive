---
title: "Karmic x64 hard locks when transferring large files to NFS mount"
date: 2010-03-24
forum: General Help
---

### Post by jeebustrain on 2010-03-24
I've got two machines, one running x64 Karmic Ubuntu Studio and one running 32bit "regular" Karmic. Both are connected via NFS mount to a third box (Openfiler) with a whole lot of disk (storing my dvd collection). I'm in the process of ripping that collection from both of my machines and transferring everything to the third box. 

The 32bit machine works great - I can transfer files to and from all day, both large and small. But the 64bit machine hard locks after about 30 minutes of transfer (I've currently got about 100GB of data that I need to get over there and it's piling up). The machine just completely hangs up with no messages on the screen (still the desktop). It completely drops off the network as well. I have to hit the reset button in order to come back. Other than this particular issue, the machine is rock solid. I've tried copying both via shell script and via Nautilus and get the same results.

Here's the only thing that I can think could be related. About a month back, I did a hardware swap (replaced mobo, cpu, and memory) and moved the previous one to that second machine (which still works fine). The x64 machine got a brand new mobo, cpu, and memory. The new nic detected itself as eth1 and I applied the same static IP address I had on the old nic. 

I've looked in /var/log/messages and haven't been able to find anything useful. Part of me is thinking that I should just wipe the box and reinstall, but I'd like to ideally wait until Lucid at least goes to RC before I do that and do a fresh install with that. 

Does anyone have any ideas about where else I could look?

---

### Post by jeebustrain on 2010-03-24
BTW - I have no idea how the Kubuntu label showed up. I tried to undo it but I can't find how to do it when I edit.

This is not Kubuntu

---

### Post by jeebustrain on 2010-03-25
ok - so per a suggestion from someone else, I ran memtest and it didn't find any errors. I got it to lock up again and these are the last bit of errors in /var/log/messages before the lockup:

```

Mar 24 00:12:32 coltrane kernel: [310907.558624] usb 1-1: USB disconnect, address 12
Mar 24 00:12:32 coltrane kernel: [310907.558632] usb 1-1.3: USB disconnect, address 14
Mar 24 01:44:25 coltrane pulseaudio[16880]: pid.c: Stale PID file, overwriting.
Mar 24 04:52:45 coltrane kernel: [327720.566202] Xorg          D ffff88011cdda478     0  2908   2907 0x00400004
Mar 24 04:52:45 coltrane kernel: [327720.566214]  ffff880125db9c08 0000000000000086 ffff880125db9bd8 ffffffff81439c02
Mar 24 04:52:45 coltrane kernel: [327720.566224]  ffff880108b8c880 ffff88011cdda0c0 ffff880125db9c08 ffff88012418c9c8
Mar 24 04:52:45 coltrane kernel: [327720.566233]  7fffffffffffffff ffff88012418c9d0 0000000000000000 0000000000000004
Mar 24 04:52:45 coltrane kernel: [327720.566242] Call Trace:
Mar 24 04:52:45 coltrane kernel: [327720.566262]  [<ffffffff81439c02>] ? __kfree_skb+0x42/0xa0
Mar 24 04:52:45 coltrane kernel: [327720.566274]  [<ffffffff8153c394>] schedule+0x14/0x30
Mar 24 04:52:45 coltrane kernel: [327720.566283]  [<ffffffff8153c685>] schedule_timeout+0x205/0x270
Mar 24 04:52:45 coltrane kernel: [327720.566292]  [<ffffffff8153b7fc>] wait_for_common+0xbc/0x180
Mar 24 04:52:45 coltrane kernel: [327720.566303]  [<ffffffff8105a770>] ? default_wake_function+0x0/0x20
Mar 24 04:52:45 coltrane kernel: [327720.566311]  [<ffffffff8153b958>] wait_for_completion+0x18/0x20
Mar 24 04:52:45 coltrane kernel: [327720.566683]  [<ffffffffa060095a>] os_acquire_sema+0x7a/0x80 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.567070]  [<ffffffffa051e543>] _nv005242rm+0x9/0xe [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.567098]  [<ffffffffa0528f1e>] ? rm_check_pci_config_space+0x1b3/0x8c6 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.567795]  [<ffffffffa05fc538>] ? nv_kern_ioctl+0xa8/0x440 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.568122]  [<ffffffffa05fc90c>] ? nv_kern_unlocked_ioctl+0x1c/0x20 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.568142]  [<ffffffff81131fdd>] ? vfs_ioctl+0x1d/0xa0
Mar 24 04:52:45 coltrane kernel: [327720.568150]  [<ffffffff81132168>] ? do_vfs_ioctl+0x78/0x3f0
Mar 24 04:52:45 coltrane kernel: [327720.568157]  [<ffffffff81122e9f>] ? vfs_read+0x12f/0x1a0
Mar 24 04:52:45 coltrane kernel: [327720.568164]  [<ffffffff81132561>] ? sys_ioctl+0x81/0xa0
Mar 24 04:52:45 coltrane kernel: [327720.568175]  [<ffffffff81012102>] ? system_call_fastpath+0x16/0x1b
Mar 24 04:52:45 coltrane kernel: [327720.568242] cp            D ffff8800c51c48f8     0 16186   3868 0x00000000
Mar 24 04:52:45 coltrane kernel: [327720.568252]  ffff880017583b08 0000000000000086 ffff880017583ab8 ffff880000000000
Mar 24 04:52:45 coltrane kernel: [327720.568261]  ffff880127b54740 ffff8800c51c4540 0000000000000286 ffff880028089f00
Mar 24 04:52:45 coltrane kernel: [327720.568269]  ffff88002804f930 ffffffff810dea80 ffff880017583bb8 0000000000000004
Mar 24 04:52:45 coltrane kernel: [327720.568278] Call Trace:
Mar 24 04:52:45 coltrane kernel: [327720.568288]  [<ffffffff810dea80>] ? sync_page+0x0/0x50
Mar 24 04:52:45 coltrane kernel: [327720.568297]  [<ffffffff8153c394>] schedule+0x14/0x30
Mar 24 04:52:45 coltrane kernel: [327720.568305]  [<ffffffff8153c3d8>] io_schedule+0x28/0x40
Mar 24 04:52:45 coltrane kernel: [327720.568312]  [<ffffffff810deabd>] sync_page+0x3d/0x50
Mar 24 04:52:45 coltrane kernel: [327720.568320]  [<ffffffff8153c8e7>] __wait_on_bit+0x57/0x80
Mar 24 04:52:45 coltrane kernel: [32772Mar 24 21:15:24 coltrane kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.



```

---

### Post by jeebustrain on 2010-03-25
here is kern.log
```

Mar 24 04:52:45 coltrane kernel: [327720.566242] Call Trace:
Mar 24 04:52:45 coltrane kernel: [327720.566262]  [<ffffffff81439c02>] ? __kfree_skb+0x42/0xa0
Mar 24 04:52:45 coltrane kernel: [327720.566274]  [<ffffffff8153c394>] schedule+0x14/0x30
Mar 24 04:52:45 coltrane kernel: [327720.566283]  [<ffffffff8153c685>] schedule_timeout+0x205/0x270
Mar 24 04:52:45 coltrane kernel: [327720.566292]  [<ffffffff8153b7fc>] wait_for_common+0xbc/0x180
Mar 24 04:52:45 coltrane kernel: [327720.566303]  [<ffffffff8105a770>] ? default_wake_function+0x0/0x20
Mar 24 04:52:45 coltrane kernel: [327720.566311]  [<ffffffff8153b958>] wait_for_completion+0x18/0x20
Mar 24 04:52:45 coltrane kernel: [327720.566683]  [<ffffffffa060095a>] os_acquire_sema+0x7a/0x80 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.567070]  [<ffffffffa051e543>] _nv005242rm+0x9/0xe [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.567098]  [<ffffffffa0528f1e>] ? rm_check_pci_config_space+0x1b3/0x8c6 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.567795]  [<ffffffffa05fc538>] ? nv_kern_ioctl+0xa8/0x440 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.568122]  [<ffffffffa05fc90c>] ? nv_kern_unlocked_ioctl+0x1c/0x20 [nvidia]
Mar 24 04:52:45 coltrane kernel: [327720.568142]  [<ffffffff81131fdd>] ? vfs_ioctl+0x1d/0xa0
Mar 24 04:52:45 coltrane kernel: [327720.568150]  [<ffffffff81132168>] ? do_vfs_ioctl+0x78/0x3f0
Mar 24 04:52:45 coltrane kernel: [327720.568157]  [<ffffffff81122e9f>] ? vfs_read+0x12f/0x1a0
Mar 24 04:52:45 coltrane kernel: [327720.568164]  [<ffffffff81132561>] ? sys_ioctl+0x81/0xa0
Mar 24 04:52:45 coltrane kernel: [327720.568175]  [<ffffffff81012102>] ? system_call_fastpath+0x16/0x1b
Mar 24 04:52:45 coltrane kernel: [327720.568230] INFO: task cp:16186 blocked for more than 120 seconds.
Mar 24 04:52:45 coltrane kernel: [327720.568236] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 24 04:52:45 coltrane kernel: [327720.568242] cp            D ffff8800c51c48f8     0 16186   3868 0x00000000
Mar 24 04:52:45 coltrane kernel: [327720.568252]  ffff880017583b08 0000000000000086 ffff880017583ab8 ffff880000000000
Mar 24 04:52:45 coltrane kernel: [327720.568261]  ffff880127b54740 ffff8800c51c4540 0000000000000286 ffff880028089f00
Mar 24 04:52:45 coltrane kernel: [327720.568269]  ffff88002804f930 ffffffff810dea80 ffff880017583bb8 0000000000000004
Mar 24 04:52:45 coltrane kernel: [327720.568278] Call Trace:
Mar 24 04:52:45 coltrane kernel: [327720.568288]  [<ffffffff810dea80>] ? sync_page+0x0/0x50
Mar 24 04:52:45 coltrane kernel: [327720.568297]  [<ffffffff8153c394>] schedule+0x14/0x30
Mar 24 04:52:45 coltrane kernel: [327720.568305]  [<ffffffff8153c3d8>] io_schedule+0x28/0x40
Mar 24 04:52:45 coltrane kernel: [327720.568312]  [<ffffffff810deabd>] sync_page+0x3d/0x50
Mar 24 04:52:45 coltrane kernel: [327720.568320]  [<ffffffff8153c8e7>] __wait_on_bit+0x57/0x80
Mar 24 04:52:45 coltrane kernel: [327720.568328]  [<ffffffff810dec2e>] wait_on_page_bit+0x6e/0x80
Mar 24 04:52:45 coltrane kernel: Mar 24 21:15:24 coltrane kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.

```

---

### Post by jeebustrain on 2010-03-26
bumpity bump?

---

### Post by TygerFish on 2011-12-04
Did you find a fix?  This sounds like the issue I've been trying to solve, which is still around on both Natty- and Oneiric-derived Mint.  When this freeze happens, the nv kernel module will sometimes also become corrupted to the point where it claims to not exist.  *apt-get --purge remove* and reinstalling fixes the GUI, but the issue persists.  I wondered if nv might have something to do with the issue and I noticed that your output includes Nvidia stuff, but it still happens without reinstalling the drivers.

I've also heard some people say using async fixes lockups for them, but it's not helping with my issue.  I'm stumped.

---

### Post by TygerFish on 2011-12-04
The UDP option seems to have fixed it for me!

---

### Post by oldos2er on 2011-12-04
Closed, necromancy.

---

