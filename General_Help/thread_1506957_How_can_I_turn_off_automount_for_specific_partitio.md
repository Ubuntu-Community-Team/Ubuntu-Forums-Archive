---
title: "How can I turn off automount for specific partition on my flash drive?"
date: 2010-06-10
forum: General Help
---

### Post by I Forgot My Username on 2010-06-10
When I refer to "automount", I think it's Gnome automount that is automounting the partition.

I have a USB with 2 partitions, one with my coding/entertainment stuff on it(/dev/sdb5 labeled "Media"), and the other with Slax Linux(/dev/sdb6, labeled "Linux").  Is there a way to get Ubuntu not to automount the one labeled "Linux", but still automount "Media"?

Thanks in advance.

---

### Post by dcstar on 2010-06-12
> **I Forgot My Username said:**
> When I refer to "automount", I think it's Gnome automount that is automounting the partition.

I have a USB with 2 partitions, one with my coding/entertainment stuff on it(/dev/sdb5 labeled "Media"), and the other with Slax Linux(/dev/sdb6, labeled "Linux").  Is there a way to get Ubuntu not to automount the one labeled "Linux", but still automount "Media"?

Thanks in advance.

No, it is all or nothing.

---

### Post by cdufour on 2010-07-22
It used to be possible using HAL policies.

Example given: cat /etc/hal/fdi/policy/my-policy.fdi
<deviceinfo version="0.2">
  <device>
    <match key="storage.serial" string="_USB_DISK_Pro_07750169010F-0:0">
      <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      <merge key="volume.policy.should_mount" type="bool">false</merge>
      <merge key="volume.ignore" type="bool">true</merge>
      <remove key="info.addons" type="strlist">hald-addon-storage</remove>
    </match>
  </device>
</deviceinfo>

Leading to: lshal
[...]
udi = '/org/freedesktop/Hal/devices/storage_serial__USB_DISK_Pro_07750169010F_0_0'
  info.addons = {} (string list)
  storage.automount_enabled_hint = false  (bool)
  volume.ignore = true  (bool)
  volume.policy.should_mount = false  (bool)
[...]

But it does not work anylonger in 10.04 Lucid Lynx (as it used to in 8.04 Hardy Heron).
In other words, Gnome/Nautilus does not honor the HAL settings anylonger.
Is it a bug? I don't know... (but it certainly gets me irred...)

---

### Post by dino99 on 2010-07-22
try mountmanager (into synaptic repo)

---

### Post by cdufour on 2010-07-22
See [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/608774](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/608774) ;-)

For a specific partition rather than an entire drive, you can use ENV{ID_FS_UUID}=="***" (see 'udevadm test /sys/block/sdX/sdXn'')

---

