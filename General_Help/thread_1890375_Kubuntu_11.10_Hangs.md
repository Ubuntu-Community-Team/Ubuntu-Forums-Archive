---
title: "Kubuntu 11.10 Hangs"
date: 2011-12-03
forum: General Help
---

### Post by gus_zernial on 2011-12-03
I have a system with Gigabyte GA-990XA-UD3 mobo, Phenom II X6 and Radeon HD 5750 graphics card, running Kubuntu 11.10, 3.0.0-13-generic kernel and fglrx from the repositories (not the Catalyst drivers downloaded from ATI).

The system is not stable and freezes (hangs) intermitently. I cannot kill X with ctrl-alt-backspace, but I can ssh in from another system and I see dmesg output like: 

INFO: rcu_sched_state detected stall on CPU 0 (t=15000 jiffies)

I´ve tried kernel 3.1.2-generic and I see the same thing. Is this a hardware/CPU problem? A kernel problem? Or ... how do I diagnose and/or fix?

Thx, Gus

---

### Post by 2F4U on 2011-12-03
Is that the only message in the file? You should take a look into /var/log/syslog since it may contain more information. I also have Phenom X6 and it runs without any problems, but I have a different motherboard and a ATI HD 4550, but I don't use the open drivers.

You should provide more details about the hangs and when they occur. If the system is not stable, there may be several reasons for it, some of the more prominent are
- issues with RAM -> run memtest
- heat issues -> verify how hot the machine is getting
- try chaning from the proprietary to the open drivers

---

