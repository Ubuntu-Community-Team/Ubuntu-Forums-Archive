---
title: "Why is postfix needed when one installs KVM?"
date: 2009-10-21
forum: General Help
---

### Post by radu.ro on 2009-10-21
Hi there,

I really don't get it why installing KVM by using these packages:
[LIST]
[*]kvm
[*]libvirt-bin
[*]ubuntu-vm-builder (aka python-vm-builder)
[*]qemu
[*]bridge-utils
[/LIST]
installs postfix too. Is it really necessary?

Thank you!

---

### Post by kushal.kumaran on 2009-10-25
Could it be because of this dependency chain?

libvirt-bin -> logrotate ->(suggests) mailx -> bsd-mailx -> postfix | mail-transport-agent

Two ways you can go from here:

- install some other mta if you have a particular dislike of postfix
- make it ignore the "Suggest" on mailx

---

### Post by radu.ro on 2009-10-25
Thank you! I haven't checked the dependency so deep but it seemed really funny to install a virtualization platform and to be hooked up with an MTA.

---

