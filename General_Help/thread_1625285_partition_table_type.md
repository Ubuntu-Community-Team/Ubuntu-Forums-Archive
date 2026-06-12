---
title: "partition table type"
date: 2010-11-18
forum: General Help
---

### Post by jsvidyad on 2010-11-18
Hello,

   When I try to partition a disk, it asks me what kind of partition table I want and gives msdos as the default. Now, if I do **_not_** want to dual-boot windows, can I choose some other partition type?  Which type would you recommend? I read that only msdos partition tables can be infected by boot-sector viruses. Is that true? Will choosing some other type of partition table protect me from boot sector viruses?

---

### Post by oldfred on 2010-11-19
One other main choice is gpt. It is used by Apple and some windows servers. It only has primary partitions and works on drives over 2TB. It allows 128 partitions (or maybe more).

MBR (msdos) has a max of 2TiB.

Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

But there is nothing really wrong with MBR(msdos) for smaller drives. You may have to use an extended partition with logicals inside the extended to have more than the 4 maximum.

---

### Post by srs5694 on 2010-11-19
Oldfred's summary is valid. I'll add that most boot sector viruses I'm aware of will mess up GRUB's ability to boot, at least if GRUB is installed in the MBR. This is true whether you use MBR or GPT partitions. This doesn't really "protect" you from boot sector viruses, but it does mean that if you *are* infected, it'll become obvious very quickly.

I'll also say that GPT has some minor advantages even on smaller disks (oldfred linked to a thread in which I elaborated on this point). OTOH, some BIOSes (particularly on Intel boards) have problems booting from GPT disks. AFAIK, these problems can always be overcome, but some people struggle with the issue if they have problems, since they aren't well documented. Overall, I'd say it's worth using GPT, particularly if you're technically savvy. If you're less technically savvy, it's more of a toss-up -- MBR is better understood by the community but has more limitations and its own pitfalls (I must have responded to dozens of threads here alone about MBR problems); whereas GPT is less well understood and has its own problems but eliminates many of MBR's more vexing issues.

---

### Post by jsvidyad on 2011-07-29
So, how do i go about using gpt on a computer with an intel motherboard?

---

### Post by mcduck on 2011-07-29
> **jsvidyad said:**
> So, how do i go about using gpt on a computer with an intel motherboard?

Start by checking your motherboards manuals and BIOS settings if it actually supports GPT partition tables. (It's quite possible that it doesn't, since like oldfred said normal PC hardware, apart from Apple machines, don't use GPT partitioning).

In general you need a machine with EFI instead of BIOS, although some BIOS systems might include support for BPT partitions.

---

### Post by srs5694 on 2011-07-29
> **mcduck said:**
> Start by checking your motherboards manuals and BIOS settings if it actually supports GPT partition tables. (It's quite possible that it doesn't, since like oldfred said normal PC hardware, apart from Apple machines, don't use GPT partitioning).

In general you need a machine with EFI instead of BIOS, although some BIOS systems might include support for BPT partitions.

This is mostly incorrect. The firmware type and the partition table type are largely independent of each other. It's possible to boot a BIOS-based computer using a GPT disk; you do *not* need EFI (or its more recent variant, UEFI) to boot from a GPT disk. You *do* need boot loader and OS support for GPT, though. The GRUB 2 that Ubuntu uses by default supports GPT booting, although you may need to create a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) to get it to work reliably. Linux, including Ubuntu, also supports GPT booting. Windows does not support booting from a GPT disk on a BIOS computer, but that's a Windows limitation, not a BIOS limitation.

There is a big caveat to all, this, though, and that is that some BIOSes have bugs that cause them to flake out when attempting to boot the computer from GPT disks. I've written up details [here.](http://www.rodsbooks.com/gdisk/bios.html) There are workarounds to some (perhaps all) such problems. Some Intel boards, in particular, have such bugs. With them, there are at least two possible workarounds or fixes:


[list]
[*]You can add the "boot" (aka the "active") flag to the protective MBR's type-0xEE partition. This is easily done with Linux's fdisk -- just use the "a" option and then save the changes with "w". Note that you must use fdisk, not parted or GParted, to do this; parted and GParted won't do what's needed in this situation.
[*]With at least some Intel boards, you can use UEFI booting rather than BIOS booting. There's a setting for this on the boot options page in the setup utility. Using this feature will require changing the boot loader and creating an EFI System Partition (ESP), if one doesn't already exist. If Ubuntu isn't yet installed, you'll have to be sure to boot the installer in UEFI mode to get the right boot loader to install.
[/list]


One more comment: Although most *existing* PCs are BIOS-based, many (perhaps most) of the motherboards introduced this year, including most or all that use Intel's Sandy Bridge CPUs, are UEFI-based. Some manufacturers try to downplay this change by using firmware interfaces that look just like old BIOS interfaces, by relying on BIOS compatibility modes for booting, and even by referring to the firmware as a "BIOS," but they are UEFI-based nonetheless.

---

