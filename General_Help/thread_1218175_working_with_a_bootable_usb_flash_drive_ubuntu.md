---
title: "working with a bootable usb flash drive ubuntu"
date: 2009-07-20
forum: General Help
---

### Post by xeth on 2009-07-20
Hi guys,

I finally got the bootable USB to work. It boots from the usb without any problems.

I have a 16gb flash drive and had it partitioned at 4gb ext4 primary and 12gb fat32 logical.

Is there a need to partition both of them as primary?

My problem is that I can't mount the 12gb fat32. There is a message "Unable to mount location - can't mount file.

using fdisk -l

  Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         486     3903763+  83  Linux
/dev/sdd2             487        1988    12064815    5  Extended
/dev/sdd5             487        1988    12064783+   b  W95 FAT32

another question is, when I paritioned the fat32, is there a difference when I choose /DOS or /WINDOWS?

Another problem I have is when using my windows vista, my dual monitors work ( my second monitor is a TV connected by S- Video )

When in Ubuntu, there is no option to configure it in the display, preferences. I'm thinking it's not supported

Thanks

---

