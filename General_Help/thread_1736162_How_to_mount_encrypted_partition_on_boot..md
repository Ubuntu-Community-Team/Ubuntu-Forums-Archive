---
title: "How to mount encrypted partition on boot."
date: 2011-04-22
forum: General Help
---

### Post by deep64blue on 2011-04-22
I have set up a LUKS encrypted partition that needs to be mounted during the boot process, the system prompts me for the pass code but then doesn't actually mount it.

When the system starts I have to unmount the encrypted device then mount -a.

This is causing issues as my Dropbox files are in the encrypted folder and it obviously can't find the files when I start.

Ubuntu 10.10 on a Thinkpad W500

/etc/crypttab
# <target name>    <source device>        <key file>    <options>
Data    /dev/sda6    none    luks,retry=1


/etc/fstab
/dev/mapper/Data    /home/alan/Data    ext3    defaults    0 0



/etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
aes-i586
dm-crypt
sha256

---

