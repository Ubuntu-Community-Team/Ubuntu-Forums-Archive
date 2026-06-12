---
title: "No countdown for grub 1.99 RC on Natty"
date: 2011-07-22
forum: General Help
---

### Post by gwu777 on 2011-07-22
Hi there,

Since earlier today, I am stuck at startup on the grub page, I have no countdown and I have to press a key to keep going. I only have Ubuntu on my PC and didn't use to view grub.

I am obviously running update-grub in between each of the modification and trying to restart...

here is my /etc/default/grub file:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

For now I would just be happy to view it for a few second, I have tried:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5

It didn't change anything, then following comments in this [bug: ]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/512593") I have done the following:
> grub-editenv /boot/grub/grubenv unset recordfail

Still no chances, any insight why my grub.cfg doesn't not seem to change and be configured correctly during update-grub would be much appreciated...

---

### Post by gwu777 on 2011-07-23
All my fault,

I have changed the way boot was mounted at startup and despite grub being updated in the boot partition, the mdr was pointing to the orginal partition with the old grub information, hence it wasn't changing when grub was updated, I couldn't be bothered to research how to change the mdr so I reseted my partition table. I am not sure if any of this make sense, but it is my case!

---

