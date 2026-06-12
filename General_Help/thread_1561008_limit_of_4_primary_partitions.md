---
title: "limit of 4 primary partitions"
date: 2010-08-25
forum: General Help
---

### Post by ubudog on 2010-08-25
Gparted:  How do I get around this?  It says to use logical partitions, but how?  (may be a noobish question, but I rarely mess with my HD)

Thank you.

---

### Post by DeMus on 2010-08-25
> **ubudog said:**
> Gparted:  How do I get around this?  It says to use logical partitions, but how?  (may be a noobish question, but I rarely mess with my HD)

Thank you.

A hard disk can contain only 4 primary partitions. To have more partitions you should add an extended partition. Inside this extended partition you can add as many logical partitions as you want. Well, sort of as many as you want, I'm sure there is a limit somewhere.

---

### Post by ubudog on 2010-08-25
Ok, cool.  Thanks.

---

### Post by srs5694 on 2010-08-25
> **DeMus said:**
> A hard disk can contain only 4 primary partitions. To have more partitions you should add an extended partition. Inside this extended partition you can add as many logical partitions as you want. Well, sort of as many as you want, I'm sure there is a limit somewhere.

This is true of the common Master Boot Record (MBR) partitioning scheme. The newer GUID Partition Table (GPT) scheme supports up to 128 partitions by default, although that number can be changed with the right software. GPT does away with the primary/extended/logical partition distinction.

In terms of the data structures, the theoretical limit on MBR logical partitions is about 2^31 (about 2 billion), but they'd all be tiny 1-sector (normally 512-byte) partitions, and you'd need a disk with 2^32 (about 4 billion) sectors to support this many partitions. If there's a lower limit in the Linux kernel, I don't know what it is. I once put about 18 or 20 logical partitions on a disk just to test it and I had no problems with that many.

---

### Post by Quackers on 2010-08-25
I think GUID partition tables can have up to 128 primary partitions but as soon as Windows is one of the installed OSes (and therefore needs an mbr) you are back to a maximum of 4 primaries.

---

### Post by ubudog on 2010-08-25
I won't be using Windows, anyway, but thanks for the reply.

---

### Post by srs5694 on 2010-08-26
> **Quackers said:**
> I think GUID partition tables can have up to 128 primary partitions but as soon as Windows is one of the installed OSes (and therefore needs an mbr) you are back to a maximum of 4 primaries.

Not exactly. GPT doesn't make the primary/extended/logical distinction, and GPT supports 128 partitions by default, as I said. Windows Vista and 7, as well as some earlier versions depending on platform, will accept such disks as data disks no matter how many partitions are defined (up to the limit of the GPT data structures on that particular disk).

The issue is that Windows will not boot from a GPT disk on a BIOS-based computer. (Thanks, Microsoft, for making life hard!) There is an ugly and dangerous hack, known as a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) that creates an illegal variant of the "protective MBR" that's part of a standard GPT configuration, in order to get around this limitation. On a hybrid MBR disk, you can have up to *three* (not four) usable partitions accessible to Windows or other GPT-unaware OSes. (The fourth MBR partition is reserved for a type-0xEE partition, which is required to get most OSes and utilities to recognize the disk as a GPT disk.) GPT-aware OSes can still access all of the GPT partitions, and will usually ignore the MBR partitions -- so you could have a dozen partitions for use by Linux, FreeBSD, MacOS X, and other sensible OSes, while Windows is confined to three partitions that it accesses via the MBR. This works because Microsoft gives precedence to MBR data structures when it sees a hybrid MBR, whereas every other GPT-aware OS gives precedence to the GPT data structures.

This is dangerous because the MBR and GPT data structures can get out of sync. For instance, suppose you set up a hybrid MBR and then use a disk utility that doesn't know about hybrid MBRs to edit the partition table. Note that "the partition table" is ambiguous here -- it could refer to either the MBR side or the GPT side. That's the point -- a partition editor for either MBR or GPT that doesn't know about hybrid MBRs can easily change the partition table so that the MBR partitions don't define partitions that occupy the same space as some or all of the GPT partitions (and vice-versa). The result would be that one OS can seriously damage another OS's partitions by accident. There are other problems that can crop up, too.

Note that when Windows installs on computers that use EFI firmware rather than a BIOS, these problems go away, since Windows supports booting from GPT on EFI-based systems. EFI is being slowly rolled out on commodity PCs, but it's still pretty rare today.

---

### Post by Quackers on 2010-08-26
srs5694, thank you for that exhaustive explanation. I was aware of some of the limitations involved when Windows was installed and also of the dangers/limitations of the hybrid MBR - but evidently not all of them :-)
I wasn't aware that Windows could install on computers using EFI without any kind of MBR/HybridMBR.
Having an OSX86 installation I have read something about EFI and GPT, but your very full explanation sheds more light on the subject.
I bow to your superior knowledge :-)

---

### Post by ubudog on 2010-08-26
Me too, lol.  Thanks for all the help guys!

---

