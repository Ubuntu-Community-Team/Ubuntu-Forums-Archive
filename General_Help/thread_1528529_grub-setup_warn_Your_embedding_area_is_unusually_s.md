---
title: "grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it."
date: 2010-07-10
forum: General Help
---

### Post by MountainX on 2010-07-10
I'm trying to install grub2 onto a USB drive.

Here's the error I'm getting:

```
# grub-install --root-directory=/tmp/temp_liveusb_root16566/usb /dev/sdf
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```

Here's how my USB drive is partitioned:
```
# fdisk -l /dev/sdf

Disk /dev/sdf: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders
Units = cylinders of 529 * 512 = 270848 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       14804     3915646+  83  Linux
```

Any ideas?

---

### Post by dcstar on 2010-07-11
> **MountainX said:**
> I'm trying to install grub2 onto a USB drive.

Here's the error I'm getting:

```
# grub-install --root-directory=**/tmp**/temp_liveusb_root16566/usb /dev/sdf
..........
```

Any ideas?

/tmp is a System folder with various restrictions and limitations, why are you using it?

---

### Post by john newbuntu on 2010-07-11
Yeah, using the local /tmp dir is one interesting thing.  If you are just trying to install grub2 to your USB, you would normally mount it and use the mountpoint or a permanent sub-directory under the mountpoint for the install.

For example, say /dev/sdf is mounted under /media/myusb, then
"sudo grub-install --root-directory=/media/myusb /dev/sdf"
should install grub2 to the MBR of your USB drive and the grub files would go under /media/usb/boot/grub/.

The other issue here I think is that your post MBR region is small enough to embed core.img.  With a logical geometry of 23 sectors/track and your partition starting at cylinder 1, I get a feeling that you do not have enough LBA's for embedding that file.  To confirm it, could you please post the output of "sudo fdisk -lu /dev/sdf".
You need around 32KB following the MBR for embedding, which means you may have to resize sdf1 or use blocklists or repartition your drive.

---

### Post by MountainX on 2010-07-11
SOLVED:

I theorized that the problem was the flash drive's geometry. See the fdisk printout and note:

23 heads, 23 sectors/track

I ran fdisk again, but this time I made the first partition start at 2 instead of the default 1. (I did not change the geometry.) This gave a little more room on the flash drive in front of the partition. Bingo, problem solved.

(So it didn't have anything to do with using /tmp.)

Postscript:
This got me thinking about partition alignment on my flash drive. The drive is a Patriot XT 4GB. I think it uses 128K erase blocks? (reference: [http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/))

As an experiment of sorts, I decided to redo the partitions and for 128k alignment. Here's how I did it in a nutshell. It works, although I did not do any benchmarking.

```
~# fdisk -l
~# mount -l
~# umount /dev/sdf*
~#  fdisk -H 224 -S 56 /dev/sdf
Command (m for help): p
Command (m for help): o
Command (m for help): p
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-624, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-624, default 624): 
Using default value 624
Command (m for help): x
Expert command (m for help): b
Partition number (1-4): 1
New beginning of data (56-7827455, default 56): 256
Expert command (m for help): r
Command (m for help): p
Command (m for help): u
Command (m for help): p
Command (m for help): a
Partition number (1-4): 1
Command (m for help): w
~# mke2fs -t ext2 -E stripe-width=32,resize=165G /dev/sdf1
~# tune2fs -c 0 -i 0 /dev/sdf1
```

references:
[http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)
[http://www.patriotmemory.com/forums/showthread.php?t=3696](http://www.patriotmemory.com/forums/showthread.php?t=3696)
and, of course:
[http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/](http://thunk.org/tytso/blog/2009/02/20/aligning-filesystems-to-an-ssds-erase-block-size/)

---

### Post by MountainX on 2010-07-11
> **john newbuntu said:**
> 
The other issue here I think is that your post MBR region is small enough to embed core.img.  With a logical geometry of 23 sectors/track and your partition starting at cylinder 1, I get a feeling that you do not have enough LBA's for embedding that file.  To confirm it, could you please post the output of "sudo fdisk -lu /dev/sdf".

You were right. I confirmed by repartitioning starting at cylinder 2, as I posted above. Thanks for your info.

---

### Post by ftzdomino on 2011-03-10
I had this problem on a Dell server.  It was fixed by deleting the Dell utility partition (which is worthless) and re-running grub-setup.  My theory is that the Dell utility partition starts at too low of a sector to give grub2 enough room to install.

---

### Post by HittingSmoke on 2012-01-07
Just an FYI for anyone coming to this post from Google as I just did.

I ran into this problem today trying to install GRUB on my 16GB USB thumb drive. After reading this post I installed gparted in Ubuntu 10.04 and move the start of the first partition up 1MB.

Fixed the problem in two minutes without reformatting the entire disk.

---

### Post by StrikerNL on 2012-01-08
> **HittingSmoke said:**
> Fixed the problem in two minutes without reformatting the entire disk.

I am trying this now, will update with result. However, how did that take two minutes for you?? It first read all data (there was 3GB, yet it did all 16GB), taking 15 minutes, now it's writing it all back, taking an estimated hour or more.

Did I do something wrong?

**Edit:** I aborted it, it soon lapsed to 1:30 and longer, so I just opted to reinstall (it was a fresh install anyhow). I repartitioned with gparted, which in fact didn't even let me start the partition at 0mb. It worked after that. IMO this is a bug in the installer, because partitioning with gparted worked straight away.

---

### Post by ullix on 2012-05-08
Thanks everyone for the discussion, as I had the same '...embedding area unusually small ...' error with my Patriot Torqx2 32GB SSD ([http://www.amazon.de/gp/product/B004XVN1U8/](http://www.amazon.de/gp/product/B004XVN1U8/) ) and could solve it with your help.

fdisk -l showed me that the 1st partition began at sector 32. When I initially installed Ubuntu 10.04 on this drive, it complained with the grub-error, but it then went ahead and used blocklists and everything worked fine. Today I tried to install Ubuntu 12.04 but it did NOT proceed with blocklists but rather stopped after reporting the error ( I did not try the --force option).

After adding some space before the 1st partition using gparted, that partition now starts at sector 63 and grub went through without error.

Some oddity in using gparted: it allows only to add 1MiB or more as preceding space to a partition, though my 31 extra sectors of 512bytes each is a whole lot less than 1 MiB. How comes???

Nevertheless, it is working fine again.

---

### Post by ledj0 on 2012-12-15
Thanks, works for me too.):P

---

