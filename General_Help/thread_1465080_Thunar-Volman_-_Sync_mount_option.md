---
title: "Thunar-Volman - Sync mount option"
date: 2010-04-29
forum: General Help
---

### Post by Rob8900 on 2010-04-29
Hi,

I want to have the sync option default on when Thunar-Volman mounts automatically my USB-stick. 

How can I do this? I've tried enabling this in the /etc/hal/fdi/policy/preferences.fdi file, but without result.


Can someone help me please? 


Rob

---

### Post by Rob8900 on 2010-05-05
up :-k

---

### Post by Splarz on 2010-05-13
not sure about your request, but i have some troubles with thunar-volman in lucid: ```
thunar --daemon
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_13fe_1f00_5B870B000133.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_13fe_1f00_5B870B000133_if0.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_13fe_1f00_5B870B000133_if0_scsi_host_0_scsi_device_lun0.
```
if i plug in an usb device i can't find it in the desktop or under resources; anyway i can acces to it just using gigolo.
do we have the same problem?

---

### Post by mr_pouit on 2010-05-13
> **Rob8900 said:**
> Hi,

I want to have the sync option default on when Thunar-Volman mounts automatically my USB-stick. 

How can I do this? I've tried enabling this in the /etc/hal/fdi/policy/preferences.fdi file, but without result.


Can someone help me please? 


Rob

You can copy /etc/xdg/xdg-xubuntu/xfce4/mount.rc (or /etc/xdg/xfce4/mount.rc) to $HOME/.config/xfce4/mount.rc, and edit it to add 'sync'.

> **Splarz said:**
> not sure about your request, but i have some troubles with thunar-volman in lucid: ```
thunar --daemon
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_13fe_1f00_5B870B000133.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_13fe_1f00_5B870B000133_if0.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_13fe_1f00_5B870B000133_if0_scsi_host_0_scsi_device_lun0.
```
if i plug in an usb device i can't find it in the desktop or under resources; anyway i can acces to it just using gigolo.
do we have the same problem?

Known bug in hal, see [https://bugs.launchpad.net/ubuntu/lucid/+source/hal/+bug/546992](https://bugs.launchpad.net/ubuntu/lucid/+source/hal/+bug/546992)

---

### Post by Splarz on 2010-05-13
thanks mr_pouit, i solved!

---

