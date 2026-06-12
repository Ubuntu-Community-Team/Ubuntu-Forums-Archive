---
title: "Modifying menu.lst when upgrading kernel"
date: 2012-06-03
forum: General Help
---

### Post by elliott94 on 2012-06-03
Hello.

I've just been upgrading packages on a machine, and noticed that a newer kernel was available. I chose to upgrade it, but during the process was notified that the local version of menu.lst had been modified.

I chose to use the version included in the latest kernel; obviously I want the option of booting from that kernel, and as far as I understand it I wouldn't be able to do this if I kept the older version of menu.lst.

What's interesting, however, is that I was asked about upgrading it twice, as can be seen below.

A new version of /boot/grub/menu.lst is available, but the version installed
currently has been locally modified.

  1. install the package maintainer's version
  2. keep the local version currently installed
  3. show the differences between the versions
  4. show a side-by-side difference between the versions
  5. show a 3-way difference between available versions
  6. do a 3-way merge between available versions (experimental)
  7. start a new shell to examine the situation

What would you like to do about menu.lst? 1


Replacing config file /var/run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz-2.6.32-41-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-38-generic-pae
A new version of /boot/grub/menu.lst is available, but the version installed
currently has been locally modified.

  1. install the package maintainer's version
  2. keep the local version currently installed
  3. show the differences between the versions
  4. show a side-by-side difference between the versions
  5. show a 3-way difference between available versions
  6. do a 3-way merge between available versions (experimental)
  7. start a new shell to examine the situation

What would you like to do about menu.lst? 1


Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


Setting up linux-image-virtual (2.6.32.41.48) ...

So, why was I asked if I wanted to replace menu.lst twice? This isn't the first time it's happened, but I'm just curious.

Thanks.

---

