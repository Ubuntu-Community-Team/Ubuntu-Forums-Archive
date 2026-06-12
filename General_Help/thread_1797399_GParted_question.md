---
title: "GParted question"
date: 2011-07-05
forum: General Help
---

### Post by joelstitch on 2011-07-05
I have 2 partitions on my hard drive one with Ubuntu and one with Windows 7. On the Ubuntu one I had 83 GB and 15GB on the Windows partition. I took off 5 GB off the Ubuntu one to added to the Windows partition and I am successful removing the 5GB (which makes a unallocated File System) But I cant add the 5GB to the Windows partition

As you can see on the attached screenshots the unallocated partition is on /dev/sda1 and I want to added to /dev/sda3. Any idea on how to do this?

---

### Post by An Sanct on 2011-07-05
> **joelstitch said:**
> I have 2 partitions on my hard drive one with Ubuntu and one with Windows 7. On the Ubuntu one I had 83 GB and 15GB on the Windows partition. I took off 5 GB off the Ubuntu one to added to the Windows partition and I am successful removing the 5GB (which makes a unallocated File System) But I cant add the 5GB to the Windows partition

As you can see on the attached screenshots the unallocated partition is on /dev/sda1 and I want to added to /dev/sda3. Any idea on how to do this?

You did notice, that in the image, the border of sda1 is not around sda3? :) that is the graphical representation of extended partitions...

HDD = SDA1 + SDA2 + SDA3

SDA1 = (sda5 + *unallocated space* + swap)
SDA2 = (system reserved)
SDA3 = (ntfs - windows)

Now, to expand your windows partition, you have to use a Live CD/USB * *preferable USB*.

And in the live session use gparted to move the swap partition next to sda5 and then resize SDA1 ... note: you have to "swap-off" the swap, to be able to move it.

After SDA1 is resized, move SDA2 to the left (next to SDA1) then move SDA3 to the left and resize it to the right, to the full extent.

That should do it :)

---

### Post by Mark Phelps on 2011-07-05
Do NOT, repeat NOT, use GParted to mess with Win7 partitions.  Doing so risks filesystem corruption which could render Win7 unbootable.

Instead, use the Win7 Disk Management utility to make any changes to Win7 partitions.  That's a lot safer way to do it.

---

### Post by dcstar on 2011-07-05
> **Mark Phelps said:**
> Do NOT, repeat NOT, use GParted to mess with Win7 partitions.  Doing so risks filesystem corruption which could render Win7 unbootable.

Instead, use the Win7 Disk Management utility to make any changes to Win7 partitions.  That's a lot safer way to do it.

I recently had a woeful time copying a working Vista partition to a backup drive and then trying to copy it back with gparted - a total failure as Vista refused to boot and required a total reinstall.

It seems that Vista/Win 7 partitions have more complications than previous Windows NTFS/DOS partitions (possibly anti-piracy stuff) and tools like gparted can't compensate for them.

Ohh, I just found this: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by An Sanct on 2011-07-05
I'd say: "Listen to Mr Phelps", he is one of the partitioning masters around here :)

So, up to windows partition movement, I still support my post, SDA1 has to be resized (make it smaller) in order to resize SDA3 (make it bigger), but avoid gparted and use windows native tools (according to people who have experience with this...)

again ... kudos, Mr Phelps! :) You helped me a lot once ;)

---

### Post by srs5694 on 2011-07-05
> **dcstar said:**
> It seems that Vista/Win 7 partitions have more complications than previous Windows NTFS/DOS partitions (possibly anti-piracy stuff) and tools like gparted can't compensate for them.  It's not "anti-piracy stuff" that's to blame; it's just absolute sector references used in the boot loader code. When you shift files around, those absolute sector references change, and the OS stops booting. The standard Windows partition resizing tool knows how to handle these changes, but GParted doesn't.  FWIW, on a UEFI-based computer, this doesn't seem to be a problem, at least judging by my limited tests. Windows booted fine even after moving the partition to a completely non-overlapping spot.

---

