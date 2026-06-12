---
title: "Ubuntu/Win-XP Dual boot - PGP encryption screwed my Ubuntu"
date: 2012-04-29
forum: General Help
---

### Post by luvshines on 2012-04-29
Hi

My life is kinda doomed ](*,)

Had an XP and Ubuntu dual boot on my office laptop. I was using Ubuntu for all the development work and Windows only for MS Office

The other day I booted into Windows and I was prompted for PGP encryption (Some office policies) and I went ahead with the installation

Now booting into Ubuntu is just not possible.
It gives me an error:> 
dev disk by-uuid does not exist dropping to shell


I booted into Live Usb and I can access my windows drive, boot partition but not the 'root' partition

I think sudo fdisk -l shows the 50GB /dev/sda8 partition but when I try to mount it, it says to specify filesystem type
-t ext4 and ext3 gives some other errors

Any idea how to solve this ?
My lot of development data and mail archives are locked in Ubuntu. Need to solve this ASAP

Thanx in advance !!

---

