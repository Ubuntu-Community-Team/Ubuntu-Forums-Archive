---
title: "KVM - Qemu doesn't seem to set up NAT"
date: 2010-05-25
forum: General Help
---

### Post by lumix on 2010-05-25
I could have sworn there was a Virtualization area in the forums, but didn't see one.

Anyway, I use:

> kvm -M pc -hda /vg0/Seven/XP.img -m 1000 -cdrom /dev/cdrom -boot c -net nic -net user

...and can ping from the host 10.x.. to the virtual router 10.x... but not outside anywhere.  Also, No route is created on the host for the 10.x... networks; shouldn't there be one?

---

