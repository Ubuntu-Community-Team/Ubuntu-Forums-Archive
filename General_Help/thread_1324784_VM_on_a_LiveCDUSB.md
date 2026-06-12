---
title: "VM on a LiveCD/USB"
date: 2009-11-12
forum: General Help
---

### Post by streetlightman on 2009-11-12
Hey everyone,

I work at a help desk at my school and we are trying to harness the power of Linux.  I've created a UNR LiveUSB.  This is what I want to do with and I was wondering if it could be done:

1.  Install a WinXP VM to it

2.  Mount (within XP) the internal hard drive of that laptop the live environment is running on.  (very important)

3.  Connect to the internet and run scans such as chkdsk or a malwarebytes scan on the mounted hard drive.

Also, while were at it, I know there is a command 'ntfsfix' in linux but i don't know what it does or how to use it.  Can someone tell me how?

Thanks!

---

### Post by lemming465 on 2009-11-13
You are probably better off for this scenario with a Windows PE 3.0 live CD/DVD/USB stick thing.  That's what the University of Wisconsin - Madison help desk built for themselves.

A vmware XP guest could probably be configured to access host drive partitions.  I'm not sure how much luck you'd have with other hypervisors.  Not that the Win PE solution is not dependent on the host hardware having any virtualization support; a lot of it doesn't.  Most non-vmware hypervisors require hardware virtualization support.

---

### Post by Giblet5 on 2009-11-13
> **lemming465 said:**
> You are probably better off for this scenario with a Windows PE 3.0 live CD/DVD/USB stick thing.  That's what the University of Wisconsin - Madison help desk built for themselves.

A vmware XP guest could probably be configured to access host drive partitions.  I'm not sure how much luck you'd have with other hypervisors.  Not that the Win PE solution is not dependent on the host hardware having any virtualization support; a lot of it doesn't.  Most non-vmware hypervisors require hardware virtualization support.

+1

I only succeeded in doing this with the Win PE and VMware methods. Just as you described and recommended.

I built the vmware stick around a 4G OCZ drive and Kubuntu 8.10. 4G proved to be barely adequate for an XP Pro vm. I'd go with 16G if I had to do this again.

You can buy prebuilt sticks at [www.pendrivelinux.com](www.pendrivelinux.com). They'll even put your school's logo on them, I think. Just install vmware and build your vm.

---

