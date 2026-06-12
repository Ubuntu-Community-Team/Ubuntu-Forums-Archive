---
title: "Windows won't boot"
date: 2009-07-07
forum: General Help
---

### Post by Altay_H on 2009-07-07
Please excuse the fact that this post relates to a problem I'm having with my Windows installation, not my Linux one.

It all started when I was partitioning my hard drive (using Ubuntu 9.04 Live CD) for a dual boot. Halfway through the process I decided to try to connect to the internet, and this caused my computer to freeze up (and the Caps Lock light to flash on and off). I had no choice but to cut the power. When I restarted, the computer would get past the BIOS with no trouble, but after that there was only a flashing _.

I was able to run a CHKDSK from the utilities offered by my BIOS and it found and corrected multiple problems, but still no progress on booting. I ran another CHKDSK which basically did the same thing, so I decided to just install Windows 7 RC over my previous install to start fresh. The installation went smoothly, but when it restarted it failed to boot.

I thought the problem might be a corrupted MBR, so I decided to use SuperGrub to fix it. SuperGrub froze up after it tried to fix the MBR and the exact same problem remained.

Finally, I decided to go back to Ubuntu to see if it could manage to boot. I installed Ubuntu and it boots properly. Unfortunately if I select Windows from my boot options in GRUB I just get the flashing underscore again.


Thank you for any help or suggestions. Right now I don't know where the problem is. I'm guessing it must be something to do with the MBR because my BIOS is working and I have a fresh Windows installation, but I have no idea how to fix it. Any help is greatly appreciated.

---

### Post by cholericfun on 2009-07-07
since you have everything fresh and (seemingly) nothing to lose on the drive i'd recommend partitioning the hard drive properly and going through the dual boot again.

i'm sure this is not what you want to hear but i'm also relativly sure that might be the healthiest option.

actually, as an afterthought:
-you ubuntu is working so MBR is working fine,
as far as i understand MBR points to you ubuntu GRUB which in turn gives you various options among others Windows (if its there)
sounds more like the boot.ini in windows is broken which is strange after a fresh install.

which brings me back to the beginning , maybe something hasn't been "partitioned off properly" on the windows part.
gpartet might help you fix this without installing anew

good luck

---

### Post by cholericfun on 2009-07-07
PS,

try this out maybe:

move some music file over to the windows partition,
play it from there,

see if you get any errors - if yes gpartet is definatly your friend

i'd still give gpartet a go to see if it finds any errors anyway btw.

---

### Post by Altay_H on 2009-07-07
> **cholericfun said:**
> since you have everything fresh and (seemingly) nothing to lose on the drive i'd recommend partitioning the hard drive properly and going through the dual boot again.
I have absolutely nothing to lose on the drive. I just want to be able to boot into Windows.

> **cholericfun said:**
> actually, as an afterthought:
-you ubuntu is working so MBR is working fine,
as far as i understand MBR points to you ubuntu GRUB which in turn gives you various options among others Windows (if its there)
sounds more like the boot.ini in windows is broken which is strange after a fresh install.
That makes sense. I thought MBR was Windows' bootloader.

> **cholericfun said:**
> move some music file over to the windows partition,
play it from there,

see if you get any errors - if yes gpartet is definatly your friend
I'll give this a try. Nautilus sees no problems with the Windows partition and displays its contents without any trouble. I'll update this post once I've tried this. Also, what do you suggest I use gparted to do? Just format the Windows partition?


EDIT: I thought I should mention that I used the system disk to do a "Startup Repair" which is supposed to fix any startup problems. It didn't find any problems and didn't fix anything.

Also, sound currently isn't working on my install, so I can't test the state of the Windows partition by playing music from it. I can browse through the files on the Windows partition though, so I can't imagine that it's actually corrupt.

---

### Post by cholericfun on 2009-07-08
gparted has a "check drive for errors" option (not sure bout the exact name you'll see it as) and it can help you fix a partition that has errors on it.

other than that, is windows on drive "C" ? 
maybe post your ```
sudo fdisk -l
```
here.

and on a different matter, i think the thread title might help you more if you mentioned "Dual boot" .

---

### Post by Altay_H on 2009-07-08
I don't see any options to check drives or partitions for errors in gparted. That sounds more like something fsck would do.


Here's my output for "sudo fdisk -l":
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43119db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24505   196836381    7  HPFS/NTFS
/dev/sda2           37253       38913    13334528    7  HPFS/NTFS
/dev/sda3           24506       37252   102390277+   5  Extended
/dev/sda5           24506       36766    98486451   83  Linux
/dev/sda6           36767       37252     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 257 MB, 257425408 bytes
8 heads, 62 sectors/track, 1013 cylinders
Units = cylinders of 496 * 512 = 253952 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         798      197903+   b  W95 FAT32
/dev/sdb2   *         799        1013       53320   83  Linux

```
The second NTFS partition on sda2 is a recovery partition. Unfortunately, since I can't boot into Windows I can't really use it.

---

### Post by karrank% on 2009-07-08
try supergrub?

---

### Post by Altay_H on 2009-07-08
> **karrank% said:**
> try supergrub?
I did, but when I use it to restore Windows to the MBR I see:
```

  Booting 'WIN => MBR & !WIN!        :((((((((((((((('

set aux_hd="hd0"
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300
dd (cd)/boot/sgd/brs/syslinux.bin (hd0) 0x1fe 0x1fe 2
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
_

```

SuperGrub does it's thing, then tries to boot Windows. The text from SuperGrub remains, and then comes the flashing underscore. Even SuperGrub is overpowered by this almighty flashing underscore problem.

---

### Post by cholericfun on 2009-07-08
> **Altay_H said:**
> t format the Windows partition?
Also, sound currently isn't working on my install, so I can't test the state of the Windows partition by playing music from it. I can browse through the files on the Windows partition though, so I can't imagine that it's actually corrupt.

i once had a problem with my windows partition, i could still see all the files et cet. in nautilus but it wouldnt actually copy/open move them once i decided to save the data and wipe the disk. gparted eventually fixed the whole thing for me.

...thats why i wanted you to check if you can actually copy stuff over and use it
for gparted use:
check this thread maybe

[http://ubuntuforums.org/showthread.php?t=1065898](http://ubuntuforums.org/showthread.php?t=1065898)

especially post #6

so your Windows partition is on the first part, good, 
not sure bout this but i find it somewhat strange that you have more than 4 partitions on one drive,
maybe something strange happened there?

---

### Post by Altay_H on 2009-07-08
> **cholericfun said:**
> i once had a problem with my windows partition, i could still see all the files et cet. in nautilus but it wouldnt actually copy/open move them once i decided to save the data and wipe the disk. gparted eventually fixed the whole thing for me.

...thats why i wanted you to check if you can actually copy stuff over and use it
for gparted use:
check this thread maybe

[http://ubuntuforums.org/showthread.php?t=1065898](http://ubuntuforums.org/showthread.php?t=1065898)

especially post #6
Now I see where the partition checking is in gparted.

Since the computer was newly purchased I just took it back to Best Buy and they're handling it now. I'll be sure to update this thread with their solution when I retrieve it in case anyone has a similar problem. Thanks for all your help and suggestions.
 
> **cholericfun said:**
> not sure bout this but i find it somewhat strange that you have more than 4 partitions on one drive,
maybe something strange happened there?
There are actually only three partitions: two primary partitions and one extended partition. The ext4 partition and swap partition are just logical partitions residing in the extended partition. A drive can only have four primary partitions, but I don't think there's any limit to the number of logical partitions it can have.

---

### Post by Altay_H on 2009-07-13
Since the events that took place to get my computer working again are significantly more complicated than I expected I'm creating a new post rather than append an edit to my previous post.

I figured that since the computer was only three days old, Best Buy would be sure to either fix the problem for me or replace the computer with another new one. I was surprised to return to hear that they determined that there was no problem with the hardware. It turns out they just ran tests on the hardware before returning it to me. The guy there suggested I try formatting the hard drive before installing Windows 7, so I figured I'd appease him before bringing it back the very next day.

I booted into Ubuntu and formatted the first partition to NTFS. I recalled that when I originally partitioned the hard drive I expanded the first partition 8 MB to the left (to use up some unallocated space), so I figured I might as well move it back while I had gparted running.

I did a fresh install of Windows 7 RC and to my surprise it booted without any issues. I figured I'd just create recovery disks using the HP utility and my still untouched recovery partition. Unfortunately HP's recovery disk creator currently doesn't work in Windows 7 RC. I figured I'd just settle for sticking with Windows 7 RC rather than a dual boot.

While searching around the web I came across something that looked promising. Someone else was having the problem of being unable to boot from their recovery partition. Someone suggested making the recovery partition "active" via an option in the context menu. I gave it a try and I was able to boot from the recovery partition at long last.

My computer is currently in the process of restoring itself to factory settings after which I'll create recovery disks and begin the process all over again. Thanks for all your help!


SHORT VERSION:
To solve the problem I simply had to format the partition to NTFS before installing Windows 7 RC over it. The 8 MB of unallocated space at the beginning of my hard drive may or may not have been a factor.

---

