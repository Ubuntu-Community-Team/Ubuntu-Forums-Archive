---
title: "Build Lucid VM with vm-builder on Hardy"
date: 2010-05-16
forum: General Help
---

### Post by pytheas22 on 2010-05-16
I have a server running Ubuntu 8.04.  I'd like to use the vm-builder utility (a.k.a. python-vm-builder, vmbuilder and ubuntu-vm-builder) to build a virtual machine image for KVM to run on this server.

I want my virtual machine to run Ubuntu 10.04, but I can't do that because the vm-builder utility only recognizes Ubuntu releases before and up to the version of Ubuntu on which the utility is run.

I'm wondering if there's a way around this without having to upgrade my server to Ubuntu 10.04, which is not really feasible at the moment.  I tried installing a more recent version of the vm-builder utility using the Lucid package, but it won't install because of unmet dependencies.

---

### Post by dcstar on 2010-05-17
> **pytheas22 said:**
> I have a server running Ubuntu 8.04.  I'd like to use the vm-builder utility (a.k.a. python-vm-builder, vmbuilder and ubuntu-vm-builder) to build a virtual machine image for KVM to run on this server.

I want my virtual machine to run Ubuntu 10.04, but I can't do that because the vm-builder utility only recognizes Ubuntu releases before and up to the version of Ubuntu on which the utility is run.

I'm wondering if there's a way around this without having to upgrade my server to Ubuntu 10.04, which is not really feasible at the moment.  I tried installing a more recent version of the vm-builder utility using the Lucid package, but it won't install because of unmet dependencies.

Build it on a different 10.04 machine.

Please put all VM related questions in the Virtualization forum.

---

