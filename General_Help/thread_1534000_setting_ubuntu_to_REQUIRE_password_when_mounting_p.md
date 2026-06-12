---
title: "setting ubuntu to REQUIRE password when mounting partitions"
date: 2010-07-18
forum: General Help
---

### Post by wriot on 2010-07-18
Hello, I remember in  Karmic by default there was a password prompt when mounting partitions.

This could be removed via  /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

and changing allow_active to "yes" under "filesystem-mount-system-internal".

It seems now in 10.04 LTS this is not the case and I can mount my partitions with no password prompt. However I would like to restore the password prompt. I have tried editing what I think is the equivalent policy file ( /usr/share/polkit-1/actions/org.freedesktop.udisks.policy ) but so far have had no luck.

I have very little experience with ubuntu so I'm not really sure what I am doing and what I should be looking for. Any ideas? Thanks.

---

### Post by sisco311 on 2010-07-19
Hi and welcome to the forums!


You shouldn't directly edit the /usr/share/polkit-1/actions/*.conf files. If you want to overwrite some settings, then create a .pkla file in /var/lib/polkit-1/localauthority/50-local.d/. i.e. Ubuntu overwrites the settings for mounting partitions in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla


Take a look at [http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html](http://hal.freedesktop.org/docs/polkit/pklocalauthority.8.html)

---

