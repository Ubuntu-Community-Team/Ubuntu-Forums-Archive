---
title: "mkinitramfs - can't find functions for scripts"
date: 2010-12-23
forum: General Help
---

### Post by NFN_NLN on 2010-12-23
Environment:
Ubuntu 10.10 Desktop

Description:
I am trying to create a custom pxe booted environment to automate the repair of systems.

I've successfully created a custom initramfs and booted it.  So far everything is working well.  I had manually added in modules, I had copied over binary tools and they do work.  The system boots fine and stops at the prompt below where I can manually perform all the tasks I need:

(initramfs) 

Problem:

1) I tried adding in custom scripts to automate the above process in "init-bottom" and "local-bottom" but they all fail saying that "panic", "log_begin_msg", "log_end_msg" don't exist.  They are in the "functions" file though.

2) It's entirely possible this is related to the root mount.  I don't want to mount a disk as a root device.  In fact I am just happy with the (initramfs) prompt.  So far I've just removed the "set root" option from grub and it just complains but continues anyways.  This could be why it can't find the functions.  Is there a way to properly fix this?



              #!/bin/sh
              PREREQ="mptctl"
              prereqs()
              {
                   echo "$PREREQ"
              }

              case $1 in
              prereqs)
                   prereqs
                   exit 0
                   ;;
              esac

              if [ ! -x "/sbin/cfggen" ]; then
                   panic "Cfggen executable not found"
              fi

              log_begin_msg "Starting mirroring"
              /sbin/cfggen ... || panic "Mirroring failed"
              log_end_msg

              exit 0

---

### Post by NFN_NLN on 2010-12-23
Simplest form:

How can I get mkinitramfs to use a ramdisk?

---

### Post by psusi on 2010-12-23
You forgot to include the functions file in your script.  Also, an initramfs IS a ramdisk.

---

### Post by NFN_NLN on 2010-12-24
> **psusi said:**
> You forgot to include the functions file in your script.  Also, an initramfs IS a ramdisk.

manually adding the functions file did work.

initramfs is a ramdisk but it keeps trying to mount a root filesystem and move the os over.  If it just booted and stayed at the prompt I'd be happy.

I tried calling initrd as follows:

initrd /boot/initrd-custom ramdisk_size=16384 root=/dev/ram0

But that doesn't work either.

---

### Post by psusi on 2010-12-24
The break=root argument ( I think it was root ) will make the script stop and drop you to the busybox shell instead of trying to mount a root fs, but that isn't very useful.  Usually people mount an NFS share as the root fs so they can boot a functioning system.

---

### Post by NFN_NLN on 2010-12-30
> **psusi said:**
> The break=root argument ( I think it was root ) will make the script stop and drop you to the busybox shell instead of trying to mount a root fs, but that isn't very useful.  Usually people mount an NFS share as the root fs so they can boot a functioning system.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thanks..  break=mount will do.

---

