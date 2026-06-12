---
title: "how do i get persistant permissions unto vmware vmnet* devices"
date: 2009-11-17
forum: General Help
---

### Post by sefs on 2009-11-17
Karmic + Udev, calling all udev experts.
It worked correctly for me under jaunty.

Here is the problem.

I installed vmware. vmnet0 was created in /dev with ownership root:root

I want to have vmnet0 with ownership root:vmware-vmnet0

So I "cp -rp /dev/vmnet0 /lib/udev/devices/" which created vmnet0 in /lib/udev/devices then I set the ownership and permissions as I want.

But on reboot vmnet0 is created in /dev with incorrect ownership and permissions and does not reflect the vmnet0 changes found in /lib/udev/devices/vmnet0.

This would have worked in jaunty but not karmic.

I filed a bug here in launchpad but do not understand what the guy was saying...

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/461275](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/461275)

---

### Post by dcstar on 2009-11-18
> **sefs said:**
> Karmic + Udev, calling all udev experts.
It worked correctly for me under jaunty.

Here is the problem.

I installed vmware. vmnet0 was created in /dev with ownership root:root

I want to have vmnet0 with ownership root:vmware-vmnet0

So I "cp -rp /dev/vmnet0 /lib/udev/devices/" which created vmnet0 in /lib/udev/devices then I set the ownership and permissions as I want.

But on reboot vmnet0 is created in /dev with incorrect ownership and permissions and does not reflect the vmnet0 changes found in /lib/udev/devices/vmnet0.

This would have worked in jaunty but not karmic.
.....

Firstly, why are you changing permissions on devices Vmware specifically sets up with the correct permissions?

Secondly, the way things work now is most likely a security fix to ensure that things cannot be hacked by someone changing permissions to what they are not supposed to be.

---

### Post by sefs on 2009-11-22
> **dcstar said:**
> Firstly, why are you changing permissions on devices Vmware specifically sets up with the correct permissions?

Secondly, the way things work now is most likely a security fix to ensure that things cannot be hacked by someone changing permissions to what they are not supposed to be.

The VMWare KB actually gives a way in how to do this.  The only oversight is that they did not take into consideration udev.  So their solution does not remain in place across reboots as udev clobbers them.  In that regards the idea that it's a security fix is unlikely since VMWare KB supports it.

---

