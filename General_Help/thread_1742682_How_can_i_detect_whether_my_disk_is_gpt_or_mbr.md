---
title: "How can i detect whether my disk is gpt or mbr"
date: 2011-04-29
forum: General Help
---

### Post by danh-a on 2011-04-29
How can i detect if my disk is formatted as gpt or mbr?

I suppose in principle this could be done by somehow
reading a few bytes (no more than say 10K) from the
beginning and possibly the end of the disk?

But there surely is a program around that does exactly
this, maybe some variation of or argument to fdisk or grub?

Thanks in advance for any info!

dan

---

### Post by tredegar on 2011-04-29
Look at it with **g**disk

---

### Post by Lars Noodén on 2011-04-29
or you can look at it with **parted** or **gparted**.

---

### Post by srs5694 on 2011-04-29
More answer than you probably wanted, but....

There are several ways. The details vary with the tool...

GPT fdisk (gdisk) provides the most complete diagnostic of partition table type that I'm aware of. Type "gdisk -l /dev/sda" (or whatever the disk is), and you'll get something like this, among other things:

```

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present

```

This tells you what partitioning data the tool has detected. In this case, it's an MBR disk. A GPT disk would look like this:

```

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

```

There's another common possibility that gdisk can detect: a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) in which a GPT disk has had MBR "copies" of up to three partitions added. This shows up in the gdisk scan as:

```

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: present

```

There are various broken configurations, too, like "MBR: MBR only" with "GPT: present", which generally means that somebody took a GPT disk and repartitioned it with fdisk or some other GPT-unaware utility. This is technically legal (it's no longer a GPT disk, but an MBR disk), but it confuses libparted-based tools such as GParted. The BSD and APM lines change if gdisk detects a BSD disklabel (usable by FreeBSD, NetBSD, etc.) or an Apple Partition Map (APM; used by 680x0- and PowerPC-based Macs).

The text-based GNU Parted reports MBR/GPT status, but not hybrid MBRs, on a line like this:

```

Partition Table: gpt

```

It uses "msdos" to mean "MBR" on this line. It reports hybrid disks as being GPT, and if you make changes it writes a fresh protective MBR, wiping out the hybrid partitions. It tends to flake out with most damaged or confused disk types, but it at least reports an error message. It can also detect and work on several other partition table types.

GParted behaves a lot like GNU Parted, but you've got to select View -> Device Information to see the partition table type.

With fdisk, you can identify GPT disks in a couple of ways. First, fdisk displays the following warning:

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk
doesn't support GPT. Use GNU Parted.

```

Second, GPT disks have a type-0xEE MBR partition, known as the "protective partition:"

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     3981311     1990655+  ee  GPT

```

This partition *must* be present on all GPT disks, but a true GPT disk contains additional data structures; so you could put such a partition on a blank disk using fdisk and it would look superficially like a GPT disk to fdisk, but it wouldn't really be a GPT disk. (The warning displayed earlier seems to check for other GPT signatures, but I've not checked the source code to learn the details.)

---

### Post by danh-a on 2011-05-02
Thanks tredegar, Lars, and srs5694.

Thanks especially srs5694, as i could check my results against your sample outputs.

This is for reference, in case somebody else needs to determine if they have a gpt or mbr disk in a situation similar to mine.  (I don't think it should be dangerous to use gdisk if you quit out of it before asking it to write anything.  But anybody please correct me if i'm wrong here.)

I saw tredegar's response first, so i decided i would try gdisk.

I could not see it as a package in Synaptic Package Manager for ubuntu 9.10, which is what i have on my machine.

But it is on source forge, and builds easily (not even a configure step), provided you install the prerequisite packages listed in the README: the uuid lib [dev version], the icu lib [dev], and libpopt [dev].  A link to the sources is in
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/)
and to a debian package in
[http://sourceforge.net/projects/gptfdisk/files/](http://sourceforge.net/projects/gptfdisk/files/)

The sources compile easily (type make and they just build).

Then all you have to do is run it,
   sudo ./gdisk
It asks you for a disk, and you give it something like /dev/sda, and
it reports ---------
you must type q after the report to make sure that it doesn't actually
do anything.

(And, in my case, i have an mbr not a gpt, which is what i thought, but wanted to be sure.)

Thanks again everybody for the replies, and if anything i've said here is wrong, please somebody correct me.

dan

---

