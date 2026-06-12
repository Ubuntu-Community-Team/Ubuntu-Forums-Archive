---
title: "Ubuntu 9.10 won't boot without old hard drive plugged in"
date: 2009-11-05
forum: General Help
---

### Post by hansamurai on 2009-11-05
Here's the short version of what's going on:

Old hard drive with Ubuntu 9.04 installed on it got some bad sectors so I'm replacing it with an identical hard drive.  I left the old hard drive plugged in so I could transfer stuff over and then installed Ubuntu 9.10 on the new drive.  Installation seemingly went successful.

Old drive: /dev/sda
New drive: /dev/sdb

9.04 and 9.10 installed on sda1 and sdb1 respectively.

I felt like I was completed with the install and file transfer, so I started packing up the old drive to send back. However, with only the new drive plugged in, the computer will not boot into anything.  I checked the BIOS and everything seems correct.  Something tells me it can't find grub.

I plugged the old drive back in and tried to boot, and it wouldn't, I had to reorder the hard drive boot order in the BIOS and put the old drive in front of the new drive, then everything booted fine.

It loads up a grub menu with first the 9.10 installation, and then all my old 9.04 kernel options.

Any help or advice? Thanks!

With a bit more searching, I managed to figure it out!

My /boot was on /dev/sda1, so I booted into the Live CD and did the following:

```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo grub-install --root-directory=/mnt/sda1 /dev/sda
```

---

