---
title: "New kernels not getting updated to GRUB list"
date: 2009-08-20
forum: General Help
---

### Post by t0mppa on 2009-08-20
Ok, I recently did a Jaunty install on this laptop and for some reason it still runs on the same kernel version (2.6.28.13) that was used when the install completed, even though there have been two later versions (.14 and .15) installed through the software updater.

They are supposed to get automatically updated to the GRUB boot list, but they never do. I suppose I could just manually edit the /etc/boot/grub/menu.lst after each update, but was curious if there's an official way to fix it.

---

### Post by plucky on 2009-08-20
> **t0mppa said:**
> Ok, I recently did a Jaunty install on this laptop and for some reason it still runs on the same kernel version (2.6.28.13) that was used when the install completed, even though there have been two later versions (.14 and .15) installed through the software updater.

They are supposed to get automatically updated to the GRUB boot list, but they never do. I suppose I could just manually edit the /etc/boot/grub/menu.lst after each update, but was curious if there's an official way to fix it.

From a terminal ```
sudo update-grub
``` should be the way to update your menu.lst file.

Usually when there is a kernel upgrade,during the upgrade it asks  you what to do with your menu.lst file.You should select the "Use package maintainers version" instead of "keep current version" (which is the default) and your menu.lst file will be updated.


Good Luck

---

### Post by mcduck on 2009-08-20
> **plucky said:**
> From a terminal ```
sudo update-grub
``` should be the way to update your menu.lst file.

Usually when there is a kernel upgrade,during the upgrade it asks  you what to do with your menu.lst file.You should select the "Use package maintainers version" instead of "keep current version" (which is the default) and your menu.lst file will be updated.


Good Luck

Actually it only asks that if you have made bad changes to the menu.lst file (like adding extra entries inside the automagic kernels list-section, or setting kernel boot options without also adding them to the default options-section.

As long as there are no problems in the menu.lst file new kernels should be added to it without any questions.

But anyway, running "sudo update-grub" should indeed fix the OP's problem. :)

---

### Post by t0mppa on 2009-08-21
Thanks for the replies, but you two slightly misunderstood my point. Granted running *update-grub* after each update is a step up from manually editing the *menu.lst* file, but what I wanted to know is why it isn't getting run during the updates from update manager and how do I fix that behavior.

```
$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-13-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

Judging from the output, it appeared that the problem was the kernels not getting properly installed. Update Manager always claimed that it installed both the headers and the images, but upon further investigation I discovered that the images never made their way to the filesystem and thus all the commotion.

Apparently the install process forgot to install the *linux-image-generic* meta package, which is in charge of getting the new images installed. Nice little bug in the installer there...

---

