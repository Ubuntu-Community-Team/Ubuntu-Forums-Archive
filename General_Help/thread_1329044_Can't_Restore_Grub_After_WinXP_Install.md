---
title: "Can't Restore Grub After WinXP Install"
date: 2009-11-17
forum: General Help
---

### Post by ram2008 on 2009-11-17
[SIZE="3"][B]Today I re-installed WinXP and then typed the following code to restore grub:

          sudo grub
          find /boot/grub/stage1

The second step produced (hd2,0). I then followed up with the following:

          root (hd2,0)
          setup (hd2,0)
          quit

After rebooting the computer, no grub menu appeared as I had expected.  The computer just booted to XP.  What did I do wrong here?  I'm running 9.04.[/B][/SIZE]

---

### Post by ranch hand on 2009-11-17
First off, do NOT post is such a manner.  It is not conducive to help.

Second run this script and post the results;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by EYESARK on 2009-11-17
you can download supergrub from [http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/) and burn the image/iso as a bootable disk
as your restart your  computer, boot from cd and you will have the option of restoring the MBR to ubuntu.

happy restoration
hope it works

---

