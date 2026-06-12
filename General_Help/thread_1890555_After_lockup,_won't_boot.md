---
title: "After lockup, won't boot"
date: 2011-12-03
forum: General Help
---

### Post by MichaelGld on 2011-12-03
I was browsing the Web with Chrome, and had a video paused when it appeared my system locked up. The mouse cursor froze and my keystrokes were ignored. I walked away for a few minutes. When I returned, my screen was dark and the system was on but non-responsive. I hard-booted the thing. I am dual booting with Windows XP (what I'm using right now). After I selected Ubuntu from the boot menu, I got the following on screen the first time, followed by something different on the second reboot.

I don't understand what's going on. Everything has been working fine up until now. Any help would be appreciated. I'm running 10.04 and just updated to the latest kernel.

---

### Post by oldtimer7777 on 2011-12-03
Are you able to boot into your Ubuntu recovery console to run the normal checks? 

> **MichaelGld said:**
> I was browsing the Web with Chrome, and had a video paused when it appeared my system locked up. The mouse cursor froze and my keystrokes were ignored. I walked away for a few minutes. When I returned, my screen was dark and the system was on but non-responsive. I hard-booted the thing. I am dual booting with Windows XP (what I'm using right now). After I selected Ubuntu from the boot menu, I got the following on screen the first time, followed by something different on the second reboot.

I don't understand what's going on. Everything has been working fine up until now. Any help would be appreciated. I'm running 10.04 and just updated to the latest kernel.

---

### Post by matt_symes on 2011-12-03
Hi

It looks like it can't mount your root filing system.

To make sure it's not a problem with a corrupted initramfs, i would first try to boot into an older kernel. This will use an older initramfs.

If that does not work the next thing i would do is boot into a LiveCD/USB and run fsck on your root partition. I would run fsck with the -N switch first to see what it makes of the partition.

If you do not have a LiveCD/USB handy you will need to make one.

Post back if you need directions.

Kind regards

---

### Post by MichaelGld on 2011-12-03
> **matt_symes said:**
> Hi

It looks like it can't mount your root filing system.

To make sure it's not a problem with a corrupted initramfs, i would first try to boot into an older kernel. This will use an older initramfs.

If that does not work the next thing i would do is boot into a LiveCD/USB and run fsck on your root partition. I would run fsck with the -N switch first to see what it makes of the partition.

If you do not have a LiveCD/USB handy you will need to make one.

Post back if you need directions.

Kind regards

Thanks for your reply. I tried booting into an older kernel and I got the same results. Now I have booted using a live cd. I ran fsck, but I'm not too familiar with all of its uses and got this:

```
ubuntu@ubuntu:/$ fsck -A
fsck from util-linux-ng 2.17.2
``` That and no more. If you could help me out a bit more, I'd really appreciate it.

Thanks

---

### Post by nm_geo on 2011-12-04
> **MichaelGld said:**
> Thanks for your reply. I tried booting into an older kernel and I got the same results. Now I have booted using a live cd. I ran fsck, but I'm not too familiar with all of its uses and got this:

```
ubuntu@ubuntu:/$ fsck -A
fsck from util-linux-ng 2.17.2
``` That and no more. If you could help me out a bit more, I'd really appreciate it.

Thanks

Try these:

From liveCD so everything is unmounted

```
sudo e2fsck -C0 -p -f -v /dev/sda5

```if errors:

```
sudo e2fsck -f -y -v /dev/sda5


```Your sdaX might not be sda5

---

### Post by MichaelGld on 2011-12-04
> **nm_geo said:**
> Try these:

From liveCD so everything is unmounted

```
sudo e2fsck -C0 -p -f -v /dev/sda5

```if errors:

```
sudo e2fsck -f -y -v /dev/sda5


```Your sdaX might not be sda5

Here's what happened:

```
ubuntu@ubuntu:/$ sudo e2fsck -C0 -p -f -v /dev/sda5
                                                                               
      12 inodes used (0.00%)
       0 non-contiguous files (0.0%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 2
   59426 blocks used (3.94%)
       0 bad blocks
       1 large file

       1 regular file
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       3 files
ubuntu@ubuntu:/$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  386313 inodes used (2.18%)
    1663 non-contiguous files (0.4%)
     406 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 353015/287/2
20868134 blocks used (29.48%)
       0 bad blocks
       2 large files

  302123 regular files
   48083 directories
      60 character device files
      26 block device files
       0 fifos
     630 links
   36007 symbolic links (32908 fast symbolic links)
       5 sockets
--------
  386934 files
ubuntu@ubuntu:/$ 
```I'll reboot now and see what happens. Thanks.

---

### Post by MichaelGld on 2011-12-05
> **nm_geo said:**
> Try these:

From liveCD so everything is unmounted

```
sudo e2fsck -C0 -p -f -v /dev/sda5

```if errors:

```
sudo e2fsck -f -y -v /dev/sda5


```Your sdaX might not be sda5

Your first suggestion worked! Upon rebooting, Ubuntu did a disk check. That required another reboot, and now everything is back to normal. Thank you very much!

---

