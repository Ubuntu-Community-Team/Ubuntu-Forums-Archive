---
title: "It boots into busybox (ash) not sure why i have dmesg output"
date: 2011-01-14
forum: General Help
---

### Post by zonemikel on 2011-01-14
I have no idea why this started to happen. My windows partition still works fine. I went in and copied the dmesg output to a text file on my windows machine and i'm posting it hear. i cant make heads or tails of it. 

I just recently did a small 13mb update ... i know i shouldnt have. Anyway somone else was logged on and i logged them off then the system hung, i had to hard reset it. Now i only get the busybox shell when i log in. 

Thanks for your time, this is the portion of the output where errors start to happen

```

[    1.037685] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.125684] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.125784] EXT4-fs (sda5): write access will be enabled during recovery
[    1.139861] EXT4-fs warning (device sda5): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    1.139998] EXT4-fs warning (device sda5): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    1.140123] BUG: unable to handle kernel paging request at 01bc0000
[    1.140218] IP: [<c035b9fa>] __percpu_counter_sum+0x2a/0x70
[    1.140296] *pde = 00000000 
[    1.140362] Oops: 0000 [#1] SMP 
[    1.140449] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:1/2:0:1:0/block/sda/sda6/uevent
[    1.140532] Modules linked in: floppy r8169 mii
[    1.140664] 
[    1.140707] Pid: 280, comm: exe Not tainted (2.6.32-27-generic #49-Ubuntu) G31-M7G DVI
[    1.140783] EIP: 0060:[<c035b9fa>] EFLAGS: 00010297 CPU: 0
[    1.140836] EIP is at __percpu_counter_sum+0x2a/0x70
[    1.140887] EAX: 00000000 EBX: 00000000 ECX: 01bc0000 EDX: 00000000
[    1.140941] ESI: 00000000 EDI: f6a5e494 EBP: f6bc5d78 ESP: f6bc5d6c
[    1.140995]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    1.141048] Process exe (pid: 280, ti=f6bc4000 task=f6a63fc0 task.ti=f6bc4000)
[    1.141121] Stack:
[    1.141163]  f6a30000 036f9c53 00000000 f6bc5dac c02a2fd6 f77fc400 f6bc5d94 c058b313
[    1.141365] <0> 00000001 f77fc400 036f9c4f 00000000 f6c190c0 f6a30000 f6a5dc00 f77fc400
[    1.141623] <0> f6bc5de4 c02a31b3 f6a30000 c05a878d c06d489c c06e3545 f6a5dc00 f6bc5de4
[    1.141919] Call Trace:
[    1.141967]  [<c02a2fd6>] ? ext4_commit_super+0xd6/0x1e0
[    1.142021]  [<c058b313>] ? printk+0x1d/0x22
[    1.142072]  [<c02a31b3>] ? ext4_clear_journal_err+0xa3/0xd0
[    1.142127]  [<c02cc5df>] ? jbd2_journal_load+0x4f/0xb0
[    1.142180]  [<c02a22d9>] ? ext4_msg+0x49/0x50
[    1.142230]  [<c02a568f>] ? ext4_load_journal+0x14f/0x2e0
[    1.142284]  [<c02a6936>] ? ext4_fill_super+0x1116/0x1930
[    1.142339]  [<c020b992>] ? get_sb_bdev+0x162/0x1a0
[    1.142391]  [<c02a5820>] ? ext4_fill_super+0x0/0x1930
[    1.142444]  [<c02a0e76>] ? ext4_get_sb+0x26/0x30
[    1.142495]  [<c02a5820>] ? ext4_fill_super+0x0/0x1930
[    1.142548]  [<c020b507>] ? vfs_kern_mount+0x67/0x170
[    1.142601]  [<c021fe43>] ? get_fs_type+0x33/0xb0
[    1.142653]  [<c020b66e>] ? do_kern_mount+0x3e/0xe0
[    1.142704]  [<c0222f83>] ? do_mount+0x1c3/0x200
[    1.142755]  [<c022302b>] ? sys_mount+0x6b/0xa0
[    1.142807]  [<c01033ec>] ? syscall_call+0x7/0xb
[    1.142859]  [<c0590000>] ? do_page_fault+0x270/0x3a0
[    1.142909] Code: 00 55 89 e5 57 89 c7 56 53 e8 d3 20 23 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 80 1d 7a c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 0c b0 59 c0 ba 
[    1.143856] EIP: [<c035b9fa>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:f6bc5d6c
[    1.143856] CR2: 0000000001bc0000
[    1.144528] ---[ end trace dd9157f2005e3cff ]---
[    1.214516] usb 2-1: configuration #1 chosen from 1 choice
[    1.456025] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    1.606541] usb 2-2: configuration #1 chosen from 1 choice
[    1.848036] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.037333] usb 5-2: configuration #1 chosen from 1 choice
[  199.956750] RPC: Registered udp transport module.
[  199.956805] RPC: Registered tcp transport module.
[  199.956855] RPC: Registered tcp NFSv4.1 backchannel transport module.
[  299.908404] attempt to access beyond end of device
[  299.908457] sda3: rw=0, want=4, limit=2
[  299.908512] EXT3-fs: unable to read superblock


```

---

### Post by zonemikel on 2011-01-14
*bump* good morning .... still very much have this issue.

---

### Post by zonemikel on 2011-01-14
Nevermind i fixed it. I booted a live cd and did a fsck.ext4 on the my root linux drive, it found some problems fixed them and now everything is honkey dorey.

---

