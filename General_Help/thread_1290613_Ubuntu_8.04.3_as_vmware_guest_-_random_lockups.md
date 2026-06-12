---
title: "Ubuntu 8.04.3 as vmware guest - random lockups"
date: 2009-10-13
forum: General Help
---

### Post by kanaida on 2009-10-13
Every few days my server locks up. I also see things in my syslog and messages inside webmin that don't look right: (got any ideas how to deal with these?)
 
I run foxpro 2.6a for unix and IBCS 3.8 so i can execute sco unix programs.
In order to compile the vmware tools and ibcs modules, i switched from linux-server image to linux-generic. that is the only kernel i found that would compile, all others bombed out.
 
here's a few things (i just show relevant lines)
 
```
Oct 13 14:53:52 scoserver kernel: [   66.696125] VMware memory control driver initialized
Oct 13 14:53:52 scoserver kernel: [   66.857881] VMCI: Major device number is: 254
Oct 13 14:53:52 scoserver kernel: [   66.961666] vsock: no version for "VMCIMemcpyToQueueV" found: kernel tainted.

```
 
 
Here's another:
 
```
 
Oct 13 00:50:14 scoserver kernel: [486547.924605] Pid: 11000, comm: vmware-guestd Tainted: GF       (2.6.24-24-generic #1)
Oct 13 00:50:14 scoserver kernel: [486547.924607] EIP: 0060:[<f8b492b3>] EFLAGS: 00000a12 CPU: 1
Oct 13 00:50:14 scoserver kernel: [486547.924616] EIP is at abi_personality+0xa3/0xd0 [abi_lcall]
Oct 13 00:50:14 scoserver kernel: [486547.924618] EAX: 00000040 EBX: 00000003 ECX: 00000002 EDX: c24c1e67
Oct 13 00:50:14 scoserver kernel: [486547.924619] ESI: f7618e86 EDI: c24c1e66 EBP: f7618e84 ESP: c24c1e58
Oct 13 00:50:14 scoserver kernel: [486547.924621]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Oct 13 00:50:14 scoserver kernel: [486547.924622] CR0: 8005003b CR2: b7f123ce CR3: 1a350000 CR4: 00000690
Oct 13 00:50:14 scoserver kernel: [486547.924624] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Oct 13 00:50:14 scoserver kernel: [486547.924626] DR6: ffff0ff0 DR7: 00000400
Oct 13 00:50:14 scoserver kernel: [486547.924641]  [anon_vma_prepare+0x5c/0xe0] anon_vma_prepare+0x5c/0xe0
Oct 13 00:50:14 scoserver kernel: [486547.924647]  [loop:kunmap_atomic+0x3d/0x2cc0] kunmap_atomic+0x3d/0xb0
Oct 13 00:50:14 scoserver kernel: [486547.924652]  [handle_mm_fault+0x567/0x730] handle_mm_fault+0x567/0x730
Oct 13 00:50:14 scoserver kernel: [486547.924654]  [ext3:do_sync_read+0xd5/0xba0] do_sync_read+0xd5/0x120
Oct 13 00:50:14 scoserver kernel: [486547.924658]  [nfs:mntput_no_expire+0x13/0x150] mntput_no_expire+0x13/0x70
Oct 13 00:50:14 scoserver kernel: [486547.924662]  [loop:kunmap_atomic+0x3d/0x2cc0] kunmap_atomic+0x3d/0xb0
Oct 13 00:50:14 scoserver kernel: [486547.924665]  [loop:kunmap_atomic+0x3d/0x2cc0] kunmap_atomic+0x3d/0xb0
Oct 13 00:50:14 scoserver kernel: [486547.924668]  [follow_page+0x15c/0x200] follow_page+0x15c/0x200
Oct 13 00:50:14 scoserver kernel: [486547.924674]  [<f8cb0022>] xout_load_object+0x22/0x8c0 [binfmt_xout]
Oct 13 00:50:14 scoserver kernel: [486547.924678]  [nfs:get_user_pages+0xdc/0x510] get_user_pages+0xdc/0x320
Oct 13 00:50:14 scoserver kernel: [486547.924684]  [get_arg_page+0x4b/0xb0] get_arg_page+0x4b/0xb0
Oct 13 00:50:14 scoserver kernel: [486547.924689]  [<f8cb0977>] xout_load_binary+0x17/0x40 [binfmt_xout]
Oct 13 00:50:14 scoserver kernel: [486547.924692]  [copy_strings+0x174/0x190] copy_strings+0x174/0x190
Oct 13 00:50:14 scoserver kernel: [486547.924695]  [<f8cb0960>] xout_load_binary+0x0/0x40 [binfmt_xout]
Oct 13 00:50:14 scoserver kernel: [486547.924698]  [search_binary_handler+0x9a/0x1e0] search_binary_handler+0x9a/0x1e0
Oct 13 00:50:14 scoserver kernel: [486547.924703]  [do_execve+0x19d/0x1d0] do_execve+0x19d/0x1d0
Oct 13 00:50:14 scoserver kernel: [486547.924707]  [sys_execve+0x2f/0x80] sys_execve+0x2f/0x80
Oct 13 00:50:14 scoserver kernel: [486547.924711]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Oct 13 00:50:14 scoserver kernel: [486547.924720]  =======================
 

```
 
I notice those messages mostly around midnight where i do some heavy nightly report generation from windows, wich uses database tables shared by samba (It's the way the setup needs to be in order to work right, FoxPro 2.6a in unix)

---

