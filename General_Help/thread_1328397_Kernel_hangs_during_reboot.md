---
title: "Kernel hangs during reboot"
date: 2009-11-16
forum: General Help
---

### Post by akernan on 2009-11-16
I did a clean install of 9.10.  When I reboot I see the following, not sure what it means.  It's also in my message log.

> 
Nov 15 14:26:58 tony-laptop kernel: [    0.002517] ------------[ cut here ]------------
Nov 15 14:26:58 tony-laptop kernel: [    0.002529] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
Nov 15 14:26:58 tony-laptop kernel: [    0.002533] Hardware name: CF-29H4LGBBM
Nov 15 14:26:58 tony-laptop kernel: [    0.002536] Modules linked in:
Nov 15 14:26:58 tony-laptop kernel: [    0.002551] Pid: 0, comm: swapper Not tainted 2.6.31-15-generic #50-Ubuntu
Nov 15 14:26:58 tony-laptop kernel: [    0.002555] Call Trace:
Nov 15 14:26:58 tony-laptop kernel: [    0.002565]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
Nov 15 14:26:58 tony-laptop kernel: [    0.002580]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
Nov 15 14:26:58 tony-laptop kernel: [    0.002586]  [<c011d7e3>] ? native_apic_write_dummy+0x33/0x40
Nov 15 14:26:58 tony-laptop kernel: [    0.002592]  [<c01451d5>] warn_slowpath_null+0x15/0x20
Nov 15 14:26:58 tony-laptop kernel: [    0.002598]  [<c011d7e3>] native_apic_write_dummy+0x33/0x40
Nov 15 14:26:58 tony-laptop kernel: [    0.002614]  [<c011278c>] intel_init_thermal+0xac/0x1a0
Nov 15 14:26:58 tony-laptop kernel: [    0.002619]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
Nov 15 14:26:58 tony-laptop kernel: [    0.002625]  [<c010fcf0>] mce_cpu_features+0x10/0x40
Nov 15 14:26:58 tony-laptop kernel: [    0.002641]  [<c056b22c>] mcheck_init+0x14a/0x188
Nov 15 14:26:58 tony-laptop kernel: [    0.002647]  [<c0569668>] ? init_hypervisor+0xb/0x2c
Nov 15 14:26:58 tony-laptop kernel: [    0.002652]  [<c0569620>] identify_cpu+0x20e/0x21d
Nov 15 14:26:58 tony-laptop kernel: [    0.002661]  [<c0795732>] identify_boot_cpu+0xd/0x23
Nov 15 14:26:58 tony-laptop kernel: [    0.002675]  [<c07958c8>] check_bugs+0xb/0xe9
Nov 15 14:26:58 tony-laptop kernel: [    0.002682]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
Nov 15 14:26:58 tony-laptop kernel: [    0.002687]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
Nov 15 14:26:58 tony-laptop kernel: [    0.002693]  [<c078e07c>] i386_start_kernel+0x7c/0x83
Nov 15 14:26:58 tony-laptop kernel: [    0.002713] ---[ end trace a7919e7f17c0a725 ]---

Any help would be appreciated.  
Thanks,
Tony

---

### Post by Giblet5 on 2009-11-16
It sounds like you have a BIOS problem affecting the APIC subsystem. There's probably a BIOS update available for that laptop.

You can probably get around this for the time being by passing the **noapic** option to your kernel (edit the grub menu entry and add "noapic" as a kernel option.

If that still doesn't fly, add "noapic" and "acpi=off" options.

Then get your BIOS update, make a MSDOS USB stick and flash your BIOS.

---

### Post by akernan on 2009-11-17
I tried the noapic & acpi=off.  I got a different trace msg.  This all started about a week ago.  I checked and I have the latest BIOS code.  I started using Karmic in Aug & I had no problems rebooting.

---

### Post by akernan on 2009-11-18
Any ideas?

---

### Post by Squideshi on 2009-11-20
I am running Ubuntu 9.10 on a Dell Inspiron 1100 laptop; and the same warning appears in my dmesg file, with the exception of minor differences in the hardware name and kernel version. The warning disappears when I use the lapic kernel parameter. Do you also see the following message earlier in your dmesg file; and if so, can you confirm that the warning disappears when you use the lapic parameter?

[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"

From what I have [read]("http://www.o3one.org/tutorials/apicarticle.txt"), my understanding is that a local APIC is built into the CPU chip and is typically used in conjunction with an I/O APIC on the motherboard for symmetric multiprocessing in multiprocessor machines but does also has some uses on uniprocessor machines.

The local APIC is normally enabled by the BIOS, but it's often not enabled by the BIOS. I'm not sure that the local APIC should be enabled on a machine where the BIOS hasn't enabled it because I don't know if it is the case that (1) the BIOS doesn't enable it simply because the BIOS author(s) never implemented it, (2) that enabling it might actually cause a problem on certain configurations, or (3) some other possibility.

Either way, I don't think we should be seeing this warning when the local APIC is disabled. This seems like a kernel bug to me. I think the next thing to do is to [file a kernel bug report]("https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies") and follow the steps on that page.

---

### Post by Squideshi on 2009-11-20
This issue has already been reported as [Ubuntu Bug #447852]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/447852") in Launchpad, already determined to be present in the upstream kernel, and has already been reported upstream.

---

