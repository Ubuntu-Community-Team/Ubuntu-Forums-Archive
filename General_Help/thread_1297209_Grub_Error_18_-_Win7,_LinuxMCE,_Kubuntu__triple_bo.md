---
title: "Grub Error 18 - Win7, LinuxMCE, Kubuntu  triple boot"
date: 2009-10-21
forum: General Help
---

### Post by NooB Frank on 2009-10-21
First - thanks in advance for the help. 

I have an old server that I have been messing with for a while.  Various flavors of linux all in the name of home theater / general pc fun.  

Recently I switched out the 40GB HD for a 160GB since it just always seemed that 40 is tight for two operating systems AND storing a couple hours of recorded tv/movies.  

So on the new HD I put Win7 on it and then loaded the latest LinuxMCE.  The Win7 worked but the new MCE didn't like my nvidia driver settings or something...  So I thought - heck I will just triple boot and add straight up kubuntu so I can see what the conf file should look like.  I know - long story but I wanted you to have the details.  

Well - Kubuntu installed nice - no issues.  I did a guided install using unused space etc.  Well - no boot.  I get Grub Error 18.  I have done some research and see what some of the answers seem to be but...  Looks like it might be a BIOS update? Or somehow playing with the MBR.  Both are a we bit scary just yet.  Plus - no one seems to be having EXACTLY my issue and it is not comfortable yet. 

Oh and - seems like my partition table is wierd.  In fact - kubuntu added it's own swap partition.  I thought multiple linux's shared the swap partition?  So I deleted the last one.  I boot from a live CD - Mepis.  Well here is my fdisk.

```
mepis1:~# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4990    39972656+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            4991       19457   116204760    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5            4991        7422    19527448+  83  Linux
/dev/sda6           18960       19457     3999208+  82  Linux swap / Solaris
/dev/sda7            7422        9960    20389288+  83  Linux

Partition table entries are not in disk order
mepis1:~# 

```

Does this look right?

How can I check up on my MBR - any data to extract from there for troubleshooting?  

Also - I am looking into the whole bios thing.  I checked and my bios is from Mar 4, 2003.  My drive shows up in Bios and again the whole machine worked before I tried for the triple boot.  How can I check if the bios is seeing my whole 160gb drive?

I have had run ins with Grub before so I am a little handy there.  Funny thing - Grub is installed on SDA5 and SDA7.  Could the MBR not know which Grub to call or??

Here is the meat of grub on SDA5 (LinuxMCE)

```

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		37a5be2a-3a04-4a31-8b21-973d6d2a9c10
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		37a5be2a-3a04-4a31-8b21-973d6d2a9c10
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		37a5be2a-3a04-4a31-8b21-973d6d2a9c10
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		37a5be2a-3a04-4a31-8b21-973d6d2a9c10
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		37a5be2a-3a04-4a31-8b21-973d6d2a9c10
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


and from SDA7 (Kubuntu)

```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		87b5abff-60a4-4305-8927-8aa15bfb3620
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87b5abff-60a4-4305-8927-8aa15bfb3620 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		87b5abff-60a4-4305-8927-8aa15bfb3620
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87b5abff-60a4-4305-8927-8aa15bfb3620 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		87b5abff-60a4-4305-8927-8aa15bfb3620
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=37a5be2a-3a04-4a31-8b21-973d6d2a9c10 ro xforcevesa single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.10, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

```


Thanks again for any help

Frank,

---

### Post by NooB Frank on 2009-10-23
Like Phil Collins says - No reply at all. 

Okay - first thing first - can someone look at my partition table and tell me if that is all okee dokey?

Thanks in advance,

---

### Post by NooB Frank on 2009-10-30
Umm... did I say something wrong?

---

