---
title: "problem of installing Xen in Eucalyptus 2.6"
date: 2012-03-15
forum: General Help
---

### Post by hayateuca on 2012-03-15
I encountered a problem when nstalling Eucalyptus 2.6. Here are the steps I followed:

I first installed the cloud controller and the node controller using 10.10 Maverick Ubuntu server

- I installed the client using desktopUbunto Maverick 10.10?

-I registered the EMI image and I am using HybridFox to to generate and manage instances

I first encountered a problem when running an instance in he node controller. The node controller has an intel i386 CPU which does not support paravirtualization of KVM and so I installed Xen instead of KVM.

After installing xen-2.6.32.32 and after when rebooting I would acess Dom0 kernel via grub, but an error message appears a startup "kernel: cannot be loaded". installing

I have been stuck in this phase and have not been able to identify the problem or fin a resolution. Any help or pointers for help would be greatly appreciated.

Thank you!

---

