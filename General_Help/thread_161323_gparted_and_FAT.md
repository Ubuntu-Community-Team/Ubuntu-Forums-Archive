---
title: "gparted and FAT"
date: 2006-04-16
forum: General Help
---

### Post by PriceChild on 2006-04-16
Hey, just a minor annoyance i've encountered a few times... why, when i format a partition as fat under gparted, does it always make it a vFat drive, so that windows cannot read it.

Does this make any sense to anyone?

Pricey

---

### Post by bernied on 2006-04-16
Windows should be able to read it - I'd always assumed FAT and VFAT were the same. gparted may not be doing the job.
Try 
mkfs.vfat /dev/hdax
replacing hdax with the name of the partition.
This worked for a shared partition on my dual boot laptop.

---

### Post by PriceChild on 2006-04-16
Hmm... its never done it automatically for me though, i've always had to use part magic to reformat the disc.

---

### Post by teasum on 2006-04-16
I use Gparted pretty much every time I do an install (including Ubuntu-only systems or dual-boot boxes).  My typical setup is small partitions for XP and Ubuntu, and then the rest of the drive as a FAT partition shared between both.  I've never had any problem with XP or Ubuntu reading the FAT partition.  Perhaps you're having an error specific to your hardware?

---

### Post by plors on 2006-04-17
internally gparted uses mkfs.vfat for creating fat filesystems, i can think of 2 reasons why gparted might not work for you:
- in old versions of gparted it didn't set the partitiontype correctly, please use the latest gparted ( [http://gparted.sourceforge.net]("http://gparted.sourceforge.net")) to be absolutely sure this isn't the cause of your problems.
- mkfs.vfat can not create bootable filesystems, from the manpage:
```

mkdosfs can not create bootable filesystems. This isn't as easy as  you
might  think at first glance for various reasons and has been discussed
a lot already.  mkdosfs simply will not support it ;)

```

If this info doesn't help you. i'd like to ask you to [file a bug]("http://gparted.sourceforge.net/bugs.php") with some 'real' evidence.

cheers :)

---

