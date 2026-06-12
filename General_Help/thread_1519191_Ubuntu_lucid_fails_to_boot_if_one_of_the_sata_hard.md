---
title: "Ubuntu lucid fails to boot if one of the sata hard disks is unplugged (not boot disk)"
date: 2010-06-27
forum: General Help
---

### Post by sammydee on 2010-06-27
So I unplugged one of my 1.5TB storage drives to lend the cable to a friend, assuming ubuntu would be able to boot fine without it. It doesn't apparently, it gets to a certain point then says a lot of ureadahead processes terminated and lists some filesystems as clean then hangs indefinitely. Same thing happens even when booted in recovery mode.

Why on earth should the removal of a hard disk only used for storage and no files integral to the system cause it to fail to boot? Any ideas?

Sam

---

### Post by pirlo89 on 2010-06-27
Im just guessing here, but you could connect the hard drive that has ubuntu with the port on the motherboard that says "sata 1".

---

### Post by sammydee on 2010-06-27
Ok so I found the problem - Lucid apparently fails to boot if any entries in the fstab do not mount/exist.

This is an absolutely ridiculous bug and I have no idea how it made it into an LTS release.

---

### Post by Ocxic on 2010-06-27
removing a drive, changes the location of the drive giving them by GRUB. GRUB is looking for drive C in a list of A,B,C,D but you removed B, which will reorder the list to A,B,C. (C becomes B, D becomes C.)

It is not a bug, your changing the hardware configuration that the system relies on.

The only entries that would cause a failed boot would be: / (root), /home. or other system partition like /etc, /var, /proc, etc..., disk's or partitions not critical to the operation of the OS would not cause the system to fail or stop booting.

Could you post the errors, or messages your getting so that we might find out what is happening.

---

### Post by wilee-nilee on 2010-06-27
> **Ocxic said:**
> removing a drive, changes the location of the drive giving them by GRUB. GRUB is looking for drive C in a list of A,B,C,D but you removed B, which will reorder the list to A,B,C. (C becomes B, D becomes C.)

It is not a bug, your changing the hardware configuration that the system relies on.

The only entries that would cause a failed boot would be: / (root), /home. or other system partition like /etc, /var, /proc, etc..., disk's or partitions not critical to the operation of the OS would not cause the system to fail or stop booting.

Could you post the errors, or messages your getting so that we might find out what is happening.

I think this is a fair assumption, post the bootscript in my signature in code tags as described.

---

### Post by sammydee on 2010-06-28
> **Ocxic said:**
> removing a drive, changes the location of the drive giving them by GRUB. GRUB is looking for drive C in a list of A,B,C,D but you removed B, which will reorder the list to A,B,C. (C becomes B, D becomes C.)

It is not a bug, your changing the hardware configuration that the system relies on.

The only entries that would cause a failed boot would be: / (root), /home. or other system partition like /etc, /var, /proc, etc..., disk's or partitions not critical to the operation of the OS would not cause the system to fail or stop booting.

Could you post the errors, or messages your getting so that we might find out what is happening.

Nope. I commented out all entries in the fstab except the root/home partition and it booted just fine. If I uncomment a non-present drive it fails to boot again.

Boot script output is attached

---

### Post by Ocxic on 2010-06-29
can you post your /etc/fstab as well

Seems GRUB is installed on 2 of your drives "sda" and "sdd"

---

### Post by sammydee on 2010-07-01
> **Ocxic said:**
> can you post your /etc/fstab as well

Seems GRUB is installed on 2 of your drives "sda" and "sdd"

I know about this, that's not the problem.

The problem was that I had turned the splash screen off and when I thought it had hanged it was actually waiting for me to press some button to ignore the error of not finding the drive in the fstab (I think).

Anyway I changed the fstab and it works now

---

