---
title: "BUG: soft lockup - CPU#0 stuck for 11s!"
date: 2009-11-04
forum: General Help
---

### Post by marcusferreira on 2009-11-04
Hello folks,
 
I have this Ubuntu Server 8.04.3 LTS running with optimized kernel 2.6.24-24-virtual for virtual machines. It's running on a VMware ESX Server 3.5 and It has VMware Tools installed. The problem is that this server is getting "locked/stuck" with the following messages. Does anyone knows if this is caused by a real bug or has been solved with any patch? 
 
Has anyone seen this?
 
```
Oct 28 20:33:39 servername kernel: [1756761.517252]  =======================
Oct 28 20:33:39 servername kernel: [1756761.529000] BUG: soft lockup - CPU#0 stuck for 11s! [swapper:0]
Oct 28 20:33:39 servername kernel: [1756761.529066] 
Oct 28 20:33:39 servername kernel: [1756761.529069] Pid: 0, comm: swapper Not tainted (2.6.24-24-virtual #1)
Oct 28 20:33:39 servername kernel: [1756761.529071] EIP: 0060:[native_safe_halt+0x2/0x10] EFLAGS: 00000246 CPU: 0
Oct 28 20:33:39 servername kernel: [1756761.529074] EIP is at native_safe_halt+0x2/0x10
Oct 28 20:33:39 servername kernel: [1756761.529076] EAX: 00000000 EBX: 00000000 ECX: c0102f30 EDX: c0406000
Oct 28 20:33:39 servername kernel: [1756761.529079] ESI: c0448004 EDI: c044e300 EBP: 000068a0 ESP: c0407fb8
Oct 28 20:33:39 servername kernel: [1756761.529081]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
Oct 28 20:33:39 servername kernel: [1756761.529083] CR0: 8005003b CR2: 0805b1e0 CR3: 1ffe8000 CR4: 00000690
Oct 28 20:33:40 servername kernel: [1756761.529085] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Oct 28 20:33:40 servername kernel: [1756761.529087] DR6: ffff0ff0 DR7: 00000400
Oct 28 20:33:40 servername kernel: [1756761.529089]  [default_idle+0x3c/0x60] default_idle+0x3c/0x60
Oct 28 20:33:40 servername kernel: [1756761.529092]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
Oct 28 20:33:40 servername kernel: [1756761.529100]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Oct 28 20:33:40 servername kernel: [1756761.529104]  [unknown_bootoption+0x0/0x1e0] unknown_bootoption+0x0/0x1e0
Oct 28 20:33:40 servername kernel: [1756761.529108]  =======================
Oct 30 15:39:17 servername kernel: [1911640.117950] console-kit-dae[6142]: segfault at 00000000 eip b7e5d5a7 esp bfb7d1e4 error 4

```Thanks in advance,
 
 
Marcus Ferreira

---

### Post by marcusferreira on 2009-11-04
Found this trick to workaround the problem. Looks like a buggy kernel for this version.

[https://bugs.launchpad.net/ubuntu/+bug/206316](https://bugs.launchpad.net/ubuntu/+bug/206316)

Thanks,

Marcus Ferreira

---

