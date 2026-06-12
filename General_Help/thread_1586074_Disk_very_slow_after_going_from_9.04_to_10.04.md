---
title: "Disk very slow after going from 9.04 to 10.04"
date: 2010-10-01
forum: General Help
---

### Post by Daniel.Ribeiro on 2010-10-01
Hi,
 
 My disk is very slow after I installed ubuntu 10.04 over my old 9.04. Doing some tinkering helped a little:
 
 > sudo hdparm -tT /dev/sda1
 
 /dev/sda1:
  Timing cached reads:   3668 MB in  2.00 seconds = 1834.11 MB/sec
  Timing buffered disk reads:  292 MB in  3.02 seconds =  96.83 MB/sec
 
 > sudo hdparm -c1 -d1 -X 66 /dev/sda1
 
 /dev/sda1:
  setting 32-bit IO_support flag to 1
  HDIO_SET_32BIT failed: Invalid argument
  setting using_dma to 1 (on)
  HDIO_SET_DMA failed: Inappropriate ioctl for device
  setting xfermode to 66 (UltraDMA mode2)
  HDIO_DRIVE_CMD(setxfermode) failed: Invalid exchange
  IO_support    =  0 (default) 
  HDIO_GET_DMA failed: Inappropriate ioctl for device
 
 > sudo hdparm -tT /dev/sda1
 
 /dev/sda1:
  Timing cached reads:   4006 MB in  2.00 seconds = 2003.29 MB/sec
  Timing buffered disk reads:  312 MB in  3.02 seconds = 103.41 MB/sec
 
 But it is still far too slow. On the other version, I had a custom  partition setup, with the home partition with 100GB, and ext3 (and other  partitions for swap, boot, root folder and space for a windows  partition I never cared to install ).
 
 This time I am using a standard Lynx setup (2 partitions, the swap  and the main one with almost 250Gb, using ext4).
 
 Some applications I develop, that use disk for some unit tests, are now  very slow to work with. Is there a way to making it faster? Going back  to 9.04? Waiting for 10,10? Gparting and making partitions smaller on  ext3? I don't know if any of these  will work....
 
 Regards,
 - Daniel

---

### Post by mörgæs on 2010-10-02
Have you tried a clean install of 9.10 on ext3?

---

### Post by Daniel.Ribeiro on 2010-10-02
Should it really be happenning? I appreciate the suggestion, but I am gonna try fsck things, a server kernel first. If things don't work out, I'll start using a memory mapped disk for tests, until maverick comes out. Then I'll try maverick first. Unless some other less drastic suggestion comes out.

If none of this solves, I'll have no other way out but try another distro.

---

