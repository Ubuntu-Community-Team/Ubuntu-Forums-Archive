---
title: "Resized / Converted an NTFS Partition on my Ubuntu Server To EXT4 Warning Message"
date: 2012-07-27
forum: General Help
---

### Post by own3mall on 2012-07-27
I resized an NTFS partition and then created an EXT4 partition with the free space on my Ubuntu server which is in a datacenter running on Ubuntu 10.04.  After going through the process through GParted, I've got a warning error that says:

> 
ERROR: Current NTFS volume size is bigger than the device size!
[IMG]http://s8.postimage.org/pcsr04zat/ubuntu_resize_error.jpg[/IMG]

This partition does not contain the boot record.  I don't really understand the error message to begin with, but what I'm really wondering is if everything will be OK if I restart the machine?  Would it be safe to restart with this error?  My new ext4 partition from this resized partition works great... Grub is the default boot loader... the windows one is called after grub if the option is selected.  Please let me know.

---

### Post by own3mall on 2012-07-28
Anyone?

---

