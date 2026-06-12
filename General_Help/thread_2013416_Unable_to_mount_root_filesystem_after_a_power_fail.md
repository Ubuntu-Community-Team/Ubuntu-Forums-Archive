---
title: "Unable to mount root filesystem after a power failure."
date: 2012-06-30
forum: General Help
---

### Post by damateem on 2012-06-30
We had a storm yesterday and the power dropped out, causing my Ubuntu server to shut off. Now, when booting, I get

[    0.564310] Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)

It  looks like a file system corruption, but I'm having a hard time fixing  the problem. I'm using Rescue Remix 12-04 to boot from USB and get  access to the system.

Using

sudo fdisk -l

Shows the hard drive as

/dev/sda1: Linux
/dev/sda2: Extended
/dev/sda5: Linux LVM

Using

sudo lvdisplay

Shows LV Names as

/dev/server1/root
/dev/server1/swap_1

Using

sudo blkid

Shows types as

/dev/sda1: ext2
/dev/sda5: LVM2_member
/dev/mapper/server1-root: ext4
/dev/mapper/server1-swap_1: swap

I  can mount sda1 and server1/root and all the files appear normal,  although I'm not really sure what issues I should be looking for. On  sda1, I see a grub folder and several other files. On root, I see the  file system as it was before I started having trouble.

I've ran the following fsck commands and none of them report any errors

sudo fsck -f /dev/sda1
sudo fsck -f /dev/server1/root
sudo fsck.ext2 -f /dev/sda1
sudo fsck.ext4 -f /dev/server1/root

and I still get the same error when the system boots.

I've hit a brick wall.

What should I try next?

What can I look at to give me a better understanding of what the problem is?

Thanks,
David

---

