---
title: "Karmic problems"
date: 2009-12-28
forum: General Help
---

### Post by akernan on 2009-12-28
I have a problem with my sound.  I hear the sound when my login screen appears.  When I login my sound is muted.  I've used Gnome & Fluxbox with the same results.  I followed this post, [http://ubuntuforums.org/showthread.php?t=789578&highlight=karmic+bugs](http://ubuntuforums.org/showthread.php?t=789578&highlight=karmic+bugs), with no change.

Any ideas?

I also have a problem rebooting.  It always hangs or I get a trace msg.  I tried 2.6.31-14 kernel with no change.  I didn't have this problem in Jaunty or when I upgraded.  I did a clean install a couple days after Karmic release and the problem started.

Any ideas?

Thanks in advance.

> 
Dec 28 09:41:27 tony-laptop kernel: [    0.001827] ------------[ cut here ]------------
Dec 28 09:41:27 tony-laptop kernel: [    0.001839] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/apic/apic.c:247 native_apic_write_dummy+0x33/0x40()
Dec 28 09:41:27 tony-laptop kernel: [    0.001843] Hardware name: CF-29H4LGBBM
Dec 28 09:41:27 tony-laptop kernel: [    0.001846] Modules linked in:
Dec 28 09:41:27 tony-laptop kernel: [    0.001853] Pid: 0, comm: swapper Not tainted 2.6.31-17-generic #54-Ubuntu
Dec 28 09:41:27 tony-laptop kernel: [    0.001856] Call Trace:
Dec 28 09:41:27 tony-laptop kernel: [    0.001868]  [<c01450fd>] warn_slowpath_common+0x6d/0xa0
Dec 28 09:41:27 tony-laptop kernel: [    0.001874]  [<c011d763>] ? native_apic_write_dummy+0x33/0x40
Dec 28 09:41:27 tony-laptop kernel: [    0.001879]  [<c011d763>] ? native_apic_write_dummy+0x33/0x40
Dec 28 09:41:27 tony-laptop kernel: [    0.001885]  [<c0145145>] warn_slowpath_null+0x15/0x20
Dec 28 09:41:27 tony-laptop kernel: [    0.001891]  [<c011d763>] native_apic_write_dummy+0x33/0x40
Dec 28 09:41:27 tony-laptop kernel: [    0.001898]  [<c011279c>] intel_init_thermal+0xac/0x1a0
Dec 28 09:41:27 tony-laptop kernel: [    0.001904]  [<c0111dcb>] mce_intel_feature_init+0xb/0x60
Dec 28 09:41:27 tony-laptop kernel: [    0.001910]  [<c010fd00>] mce_cpu_features+0x10/0x40
Dec 28 09:41:27 tony-laptop kernel: [    0.001918]  [<c056b14c>] mcheck_init+0x14a/0x188
Dec 28 09:41:27 tony-laptop kernel: [    0.001923]  [<c0569598>] ? init_hypervisor+0xb/0x2c
Dec 28 09:41:27 tony-laptop kernel: [    0.001928]  [<c0569550>] identify_cpu+0x20e/0x21d
Dec 28 09:41:27 tony-laptop kernel: [    0.001937]  [<c0795732>] identify_boot_cpu+0xd/0x23
Dec 28 09:41:27 tony-laptop kernel: [    0.001942]  [<c07958c8>] check_bugs+0xb/0xe9
Dec 28 09:41:27 tony-laptop kernel: [    0.001949]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
Dec 28 09:41:27 tony-laptop kernel: [    0.001955]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
Dec 28 09:41:27 tony-laptop kernel: [    0.001961]  [<c078e07c>] i386_start_kernel+0x7c/0x83
Dec 28 09:41:27 tony-laptop kernel: [    0.001972] ---[ end trace a7919e7f17c0a725 ]---


---

### Post by akernan on 2009-12-28
I followed this [Bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/447852") and added lapic to the boot, but it made no difference.  I still get a trace msg when I reboot.

---

### Post by akernan on 2009-12-29
After a couple reboots my trace msg has disappeared.  I added lapic to the kernel cmd in grub.  Not sure why it took a couple reboots to take affect.

I still have the sound problem.  Any ideas about that?

---

### Post by akernan on 2009-12-31
Can anybody help with sound issue?

---

### Post by akernan on 2009-12-31
I made the change suggest in #77 of this [bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732").  This fixed my sound problem.

I'm still having a problem with a trace msg on reboot.  My system reboots w/o a problem sometimes, sometimes I get a trace immediately, other times I get a trace after a couple mins of hanging during a reboot.  My hard drive light isn't flashhing at this time.  I'd like to know what this trace msg means.

---

