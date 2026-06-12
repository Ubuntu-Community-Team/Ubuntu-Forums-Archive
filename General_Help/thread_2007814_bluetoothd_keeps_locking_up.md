---
title: "bluetoothd keeps locking up"
date: 2012-06-21
forum: General Help
---

### Post by js54 on 2012-06-21
I am having problems with the bluetooth daemon on 12.04 64bit.  I am pairing a Wiimote using the gnome-bluetooth utility.  The initial pairing works fine.  If I shutoff the wiimote and turn it back on, the bluetooth daemon locks up.  I cannot kill it and the system hangs when I try and reboot.  I have to physically power off the system to get bluetooth working again.  

I see the same error in the last three kernels on my system 3.2.0-20-generic, 3.2.0-24-generic, and 3.2.0-25-generic kernel.    It seems to occur more frequently in the latest kernel (3.2.0-25-generic)

Below is the syslog errors I am seeing.  Any ideas?

Here is the error I see in the syslog when it happens:
```
Jun 21 11:20:45 milhouse kernel: [  178.172233] ------------[ cut here ]------------
Jun 21 11:20:45 milhouse kernel: [  178.172242] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_add_one+0xc0/0xf0()
Jun 21 11:20:45 milhouse kernel: [  178.172244] Hardware name: Precision WorkStation T3400  
Jun 21 11:20:45 milhouse kernel: [  178.172247] sysfs: cannot create duplicate filename '/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/bluetooth/hci0/hci0:11'
Jun 21 11:20:45 milhouse kernel: [  178.172249] Modules linked in: hid_wiimote ff_memless hidp vesafb rfcomm bnep snd_hda_codec_analog nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd ppdev btusb bluetooth joydev soundcore snd_page_alloc x38_edac dcdbas edac_core mac_hid parport_pc psmouse lp serio_raw parport usbhid hid tg3
Jun 21 11:20:45 milhouse kernel: [  178.172290] Pid: 51, comm: kworker/u:6 Tainted: P           O 3.2.0-20-generic #33-Ubuntu
Jun 21 11:20:45 milhouse kernel: [  178.172293] Call Trace:
Jun 21 11:20:45 milhouse kernel: [  178.172299]  [<ffffffff8106726f>] warn_slowpath_common+0x7f/0xc0
Jun 21 11:20:45 milhouse kernel: [  178.172303]  [<ffffffff81067366>] warn_slowpath_fmt+0x46/0x50
Jun 21 11:20:45 milhouse kernel: [  178.172307]  [<ffffffff811ed770>] sysfs_add_one+0xc0/0xf0
Jun 21 11:20:45 milhouse kernel: [  178.172310]  [<ffffffff811ed817>] create_dir+0x77/0xd0
Jun 21 11:20:45 milhouse kernel: [  178.172313]  [<ffffffff811ed91d>] sysfs_create_dir+0x7d/0xc0
Jun 21 11:20:45 milhouse kernel: [  178.172318]  [<ffffffff8130c861>] kobject_add_internal+0xb1/0x200
Jun 21 11:20:45 milhouse kernel: [  178.172322]  [<ffffffff8130cd27>] kobject_add+0x67/0xc0
Jun 21 11:20:45 milhouse kernel: [  178.172327]  [<ffffffff8116324c>] ? kmem_cache_alloc_trace+0x10c/0x140
Jun 21 11:20:45 milhouse kernel: [  178.172332]  [<ffffffff813f1f7d>] device_add+0xfd/0x3e0
Jun 21 11:20:45 milhouse kernel: [  178.172336]  [<ffffffff813f1e5b>] ? device_private_init+0x5b/0x80
Jun 21 11:20:45 milhouse kernel: [  178.172348]  [<ffffffffa010ca10>] ? __match_tty+0x40/0x40 [bluetooth]
Jun 21 11:20:45 milhouse kernel: [  178.172356]  [<ffffffffa010ca73>] add_conn+0x63/0x120 [bluetooth]
Jun 21 11:20:45 milhouse kernel: [  178.172363]  [<ffffffffa010ca10>] ? __match_tty+0x40/0x40 [bluetooth]
Jun 21 11:20:45 milhouse kernel: [  178.172368]  [<ffffffff81084e5a>] process_one_work+0x11a/0x480
Jun 21 11:20:45 milhouse kernel: [  178.172372]  [<ffffffff81085c04>] worker_thread+0x164/0x370
Jun 21 11:20:45 milhouse kernel: [  178.172375]  [<ffffffff81085aa0>] ? manage_workers.isra.29+0x130/0x130
Jun 21 11:20:45 milhouse kernel: [  178.172379]  [<ffffffff8108a45c>] kthread+0x8c/0xa0
Jun 21 11:20:45 milhouse kernel: [  178.172384]  [<ffffffff81666674>] kernel_thread_helper+0x4/0x10
Jun 21 11:20:45 milhouse kernel: [  178.172388]  [<ffffffff8108a3d0>] ? flush_kthread_worker+0xa0/0xa0
Jun 21 11:20:45 milhouse kernel: [  178.172397]  [<ffffffff81666670>] ? gs_change+0x13/0x13
Jun 21 11:20:45 milhouse kernel: [  178.172398] ---[ end trace dde993e02d3aaea9 ]---
Jun 21 11:20:45 milhouse kernel: [  178.172401] kobject_add_internal failed for hci0:11 with -EEXIST, don't try to register things with the same name in the same directory.
Jun 21 11:20:45 milhouse kernel: [  178.172404] Pid: 51, comm: kworker/u:6 Tainted: P        W  O 3.2.0-20-generic #33-Ubuntu
Jun 21 11:20:45 milhouse kernel: [  178.172406] Call Trace:
Jun 21 11:20:45 milhouse kernel: [  178.172408]  [<ffffffff8130c905>] kobject_add_internal+0x155/0x200
Jun 21 11:20:45 milhouse kernel: [  178.172411]  [<ffffffff8130cd27>] kobject_add+0x67/0xc0
Jun 21 11:20:45 milhouse kernel: [  178.172413]  [<ffffffff8116324c>] ? kmem_cache_alloc_trace+0x10c/0x140
Jun 21 11:20:45 milhouse kernel: [  178.172416]  [<ffffffff813f1f7d>] device_add+0xfd/0x3e0
Jun 21 11:20:45 milhouse kernel: [  178.172418]  [<ffffffff813f1e5b>] ? device_private_init+0x5b/0x80
Jun 21 11:20:45 milhouse kernel: [  178.172423]  [<ffffffffa010ca10>] ? __match_tty+0x40/0x40 [bluetooth]
Jun 21 11:20:45 milhouse kernel: [  178.172428]  [<ffffffffa010ca73>] add_conn+0x63/0x120 [bluetooth]
Jun 21 11:20:45 milhouse kernel: [  178.172432]  [<ffffffffa010ca10>] ? __match_tty+0x40/0x40 [bluetooth]
Jun 21 11:20:45 milhouse kernel: [  178.172435]  [<ffffffff81084e5a>] process_one_work+0x11a/0x480
Jun 21 11:20:45 milhouse kernel: [  178.172437]  [<ffffffff81085c04>] worker_thread+0x164/0x370
Jun 21 11:20:45 milhouse kernel: [  178.172440]  [<ffffffff81085aa0>] ? manage_workers.isra.29+0x130/0x130
Jun 21 11:20:45 milhouse kernel: [  178.172442]  [<ffffffff8108a45c>] kthread+0x8c/0xa0
Jun 21 11:20:45 milhouse kernel: [  178.172444]  [<ffffffff81666674>] kernel_thread_helper+0x4/0x10
Jun 21 11:20:45 milhouse kernel: [  178.172447]  [<ffffffff8108a3d0>] ? flush_kthread_worker+0xa0/0xa0
Jun 21 11:20:45 milhouse kernel: [  178.172449]  [<ffffffff81666670>] ? gs_change+0x13/0x13
Jun 21 11:20:45 milhouse kernel: [  178.172451] Bluetooth: Failed to register connection device
Jun 21 11:20:50 milhouse kernel: [  183.596429] BUG: unable to handle kernel NULL pointer dereference at 0000000000000079
Jun 21 11:20:50 milhouse kernel: [  183.596433] IP: [<ffffffff811ed8d5>] sysfs_create_dir+0x35/0xc0
Jun 21 11:20:50 milhouse kernel: [  183.596440] PGD 0 
Jun 21 11:20:50 milhouse kernel: [  183.596442] Oops: 0000 [#1] SMP 
Jun 21 11:20:50 milhouse kernel: [  183.596445] CPU 0 
Jun 21 11:20:50 milhouse kernel: [  183.596446] Modules linked in: hid_wiimote ff_memless hidp vesafb rfcomm bnep snd_hda_codec_analog nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd ppdev btusb bluetooth joydev soundcore snd_page_alloc x38_edac dcdbas edac_core mac_hid parport_pc psmouse lp serio_raw parport usbhid hid tg3
Jun 21 11:20:50 milhouse kernel: [  183.596471] 
Jun 21 11:20:50 milhouse kernel: [  183.596473] Pid: 825, comm: bluetoothd Tainted: P        W  O 3.2.0-20-generic #33-Ubuntu Dell Inc. Precision WorkStation T3400  /0TP412
Jun 21 11:20:50 milhouse kernel: [  183.596477] RIP: 0010:[<ffffffff811ed8d5>]  [<ffffffff811ed8d5>] sysfs_create_dir+0x35/0xc0
Jun 21 11:20:50 milhouse kernel: [  183.596480] RSP: 0018:ffff880214aa5ab8  EFLAGS: 00010246
Jun 21 11:20:50 milhouse kernel: [  183.596482] RAX: ffff880212d551b0 RBX: ffff880202aaf8b0 RCX: ffff880202aaf8b8
Jun 21 11:20:50 milhouse kernel: [  183.596484] RDX: ffff8802157e8c18 RSI: 0000000000000000 RDI: ffff880202aaf8b0
Jun 21 11:20:50 milhouse kernel: [  183.596486] RBP: ffff880214aa5ae8 R08: 0000000000000000 R09: ffff8802155c59c0
Jun 21 11:20:50 milhouse kernel: [  183.596487] R10: ffff8802155c59c0 R11: ffffc90000002000 R12: 0000000000000000
Jun 21 11:20:50 milhouse kernel: [  183.596489] R13: 0000000000000000 R14: ffff880202aafb00 R15: 00000000ffffffea
Jun 21 11:20:50 milhouse kernel: [  183.596491] FS:  00007f9db72e2740(0000) GS:ffff88023bc00000(0000) knlGS:0000000000000000
Jun 21 11:20:50 milhouse kernel: [  183.596493] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 21 11:20:50 milhouse kernel: [  183.596495] CR2: 0000000000000079 CR3: 00000002133ef000 CR4: 00000000000006f0
Jun 21 11:20:50 milhouse kernel: [  183.596497] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 21 11:20:50 milhouse kernel: [  183.596498] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 21 11:20:50 milhouse kernel: [  183.596500] Process bluetoothd (pid: 825, threadinfo ffff880214aa4000, task ffff880214addbc0)
Jun 21 11:20:50 milhouse kernel: [  183.596502] Stack:
Jun 21 11:20:50 milhouse kernel: [  183.596503]  ffff880214aa5ad8 ffff8802330235b8 ffff880214aa5ae8 ffff880202aaf8b0
Jun 21 11:20:50 milhouse kernel: [  183.596507]  ffff880212d551b0 0000000000000000 ffff880214aa5b28 ffffffff8130c861
Jun 21 11:20:50 milhouse kernel: [  183.596510]  ffff880214aa5b38 ffff880202aaf8b0 ffff880212d551b0 0000000000000000
Jun 21 11:20:50 milhouse kernel: [  183.596513] Call Trace:
Jun 21 11:20:50 milhouse kernel: [  183.596519]  [<ffffffff8130c861>] kobject_add_internal+0xb1/0x200
Jun 21 11:20:50 milhouse kernel: [  183.596521]  [<ffffffff8130cd27>] kobject_add+0x67/0xc0
Jun 21 11:20:50 milhouse kernel: [  183.596525]  [<ffffffff813f1f7d>] device_add+0xfd/0x3e0
Jun 21 11:20:50 milhouse kernel: [  183.596531]  [<ffffffffa0030d92>] hid_add_device+0x82/0x110 [hid]
Jun 21 11:20:50 milhouse kernel: [  183.596534]  [<ffffffffa01ab05b>] hidp_add_connection+0x33b/0x580 [hidp]
Jun 21 11:20:50 milhouse kernel: [  183.596538]  [<ffffffff8108aef0>] ? add_wait_queue+0x60/0x60
Jun 21 11:20:50 milhouse kernel: [  183.596540]  [<ffffffffa01ab841>] hidp_sock_ioctl+0x241/0x2d0 [hidp]
Jun 21 11:20:50 milhouse kernel: [  183.596544]  [<ffffffff8129db26>] ? security_sk_alloc+0x16/0x20
Jun 21 11:20:50 milhouse kernel: [  183.596547]  [<ffffffff8152d113>] ? sk_prot_alloc+0x83/0x210
Jun 21 11:20:50 milhouse kernel: [  183.596551]  [<ffffffff8116324c>] ? kmem_cache_alloc_trace+0x10c/0x140
Jun 21 11:20:50 milhouse kernel: [  183.596554]  [<ffffffff812d612c>] ? apparmor_file_alloc_security+0x2c/0x60
Jun 21 11:20:50 milhouse kernel: [  183.596557]  [<ffffffff81526ba0>] sock_do_ioctl+0x30/0x70
Jun 21 11:20:50 milhouse kernel: [  183.596560]  [<ffffffff81528059>] sock_ioctl+0x79/0x2f0
Jun 21 11:20:50 milhouse kernel: [  183.596563]  [<ffffffff81189d2a>] do_vfs_ioctl+0x8a/0x340
Jun 21 11:20:50 milhouse kernel: [  183.596565]  [<ffffffff8118a071>] sys_ioctl+0x91/0xa0
Jun 21 11:20:50 milhouse kernel: [  183.596567]  [<ffffffff81529e60>] ? sys_socket+0x40/0x70
Jun 21 11:20:50 milhouse kernel: [  183.596570]  [<ffffffff81664502>] system_call_fastpath+0x16/0x1b
Jun 21 11:20:50 milhouse kernel: [  183.596572] Code: 83 ec 18 66 66 66 66 90 48 85 ff 48 89 fb 0f 84 98 00 00 00 48 8b 47 18 49 c7 c4 e0 fc c4 81 48 85 c0 74 04 4c 8b 60 30 45 31 ed <41> 80 7c 24 79 00 75 5b 48 89 df e8 0b fa 11 00 48 85 c0 74 66 
Jun 21 11:20:50 milhouse kernel: [  183.596599] RIP  [<ffffffff811ed8d5>] sysfs_create_dir+0x35/0xc0
Jun 21 11:20:50 milhouse kernel: [  183.596602]  RSP <ffff880214aa5ab8>
Jun 21 11:20:50 milhouse kernel: [  183.596603] CR2: 0000000000000079
Jun 21 11:20:50 milhouse kernel: [  183.596606] ---[ end trace dde993e02d3aaeaa ]---
Jun 21 11:20:50 milhouse bluez: Stopping uarts
Jun 21 11:20:50 milhouse kernel: [  183.636243] init: bluetooth main process (825) killed by KILL signal
Jun 21 11:20:50 milhouse kernel: [  183.636270] init: bluetooth main process ended, respawning
Jun 21 11:20:50 milhouse bluez: Stopping rfcomm
Jun 21 11:20:50 milhouse bluetoothd[2894]: Bluetooth daemon 4.98
Jun 21 11:20:50 milhouse bluetoothd[2894]: Starting SDP server
Jun 21 11:20:50 milhouse bluetoothd[2894]: Failed to init alert plugin
Jun 21 11:20:50 milhouse bluetoothd[2894]: Failed to init time plugin
Jun 21 11:20:50 milhouse bluetoothd[2894]: Failed to init proximity plugin
Jun 21 11:20:50 milhouse bluetoothd[2894]: Failed to init gatt_example plugin
Jun 21 11:20:50 milhouse bluetoothd[2894]: Listening for HCI events on hci0
Jun 21 11:20:50 milhouse bluetoothd[2894]: HCI dev 0 up
Jun 21 11:20:50 milhouse bluetoothd[2894]: Adapter /org/bluez/2894/hci0 has been enabled
Jun 21 11:20:50 milhouse bluetoothd[2894]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/HFPAG
Jun 21 11:20:50 milhouse bluetoothd[2894]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSource
Jun 21 11:20:50 milhouse bluetoothd[2894]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/A2DPSink
Jun 21 11:25:24 milhouse AptDaemon: INFO: Quitting due to inactivity
Jun 21 11:25:24 milhouse AptDaemon: INFO: Quitting was requested

```

---

### Post by js54 on 2012-07-05
I should add that if I run 'sudo stop bluetooth' after this error occurs, the command never returns.  It appears any attempts to shutdown the bluetooth service hang.  This is what is causing a system reboot or shutdown to hang.  

Thanks.

---

### Post by js54 on 2012-07-12
I figured out what was causing the problem.  When a bluetooth device was connected it would create a directory:

/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/bluetooth/hci0/hci0:12/0005:057E:0306.000C/input/input31

When a device disconnects, eventually this directory is removed.   However, if you immediately try to re-pair the same device before this  directory is removed.  The kernel panic error happens and the bluetoothd  locks up and stops responding.   If I wait for this directory to be  removed then re-pair the device, I don't receive the kernel panic errors  and bluetoothd functions normally. I can reliable reproduce this error through the last several kernel versions.  

I am not sure if this information is useful for you but I thought I would pass it along.

A bug still exists because the kernel/bluetoothd should be able to resolve this issue and prevent the lockup.  But for my purposes, this problem is fixed.  Thanks.

---

