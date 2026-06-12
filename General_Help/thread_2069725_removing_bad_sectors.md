---
title: "removing bad sectors"
date: 2012-10-11
forum: General Help
---

### Post by eslam elbyaly on 2012-10-11
i have kubuntu , i wanna remove my hd bad sectors , and i have ubuntu live cd too , can i do this with anyone of them?

---

### Post by bra|10n on 2012-10-11
> A **bad sector** is a [sector]("http://en.wikipedia.org/wiki/Disk_sector") on a computer's [disk drive]("http://en.wikipedia.org/wiki/Disk_drive") or [flash memory]("http://en.wikipedia.org/wiki/Flash_memory")  that cannot be used due to **permanent** damage (or an OS inability to  successfully access it), such as physical damage to the disk surface (or  sometimes sectors being stuck in a magnetic or digital state that  cannot be reversed) or failed flash memory transistors. It is usually  detected by a disk utility software such as [CHKDSK]("http://en.wikipedia.org/wiki/CHKDSK") or [SCANDISK]("http://en.wikipedia.org/wiki/SCANDISK") on Microsoft systems, or [badblocks]("http://en.wikipedia.org/wiki/Badblocks")  on Unix-like systems. When found, these programs may mark the sectors  unusable (all file systems contain provisions for bad-sector marks) and  the [operating system]("http://en.wikipedia.org/wiki/Operating_system") skips them in the future.Note the word **permanent**, and the word repair is not mentioned anywhere...

[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

---

### Post by eslam elbyaly on 2012-10-11
> **bra|10n said:**
> Note the word **permanent**, and the word repair is not mentioned anywhere...

[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

so sorry ,but please help me directly , i am writing on my bad mobile.
i wanna make them unusable.
i want an alternative for chkdsk ,bad blocks.
thanks

---

### Post by shreepads on 2012-10-11
Assuming it's ext2/3/4 start the Live CD and run:

sudo e2fsck -cf /dev/sda1 <replace with correct partition name>

First see: [http://manpages.ubuntu.com/manpages/precise/man8/fsck.ext2.8.html](http://manpages.ubuntu.com/manpages/precise/man8/fsck.ext2.8.html)

---

### Post by eslam elbyaly on 2012-10-11
> **shreepads said:**
> Assuming it's ext2/3/4 start the Live CD and run:

sudo e2fsck -cf /dev/sda1 <replace with correct partition name>

First see: [http://manpages.ubuntu.com/manpages/precise/man8/fsck.ext2.8.html](http://manpages.ubuntu.com/manpages/precise/man8/fsck.ext2.8.html)

it is fat32 but i think the pc i've got has the kubuntu inside it or inside another partition. it was installed incorrectly . and i do not know if it is sda1/2/3, beside this , gparted does not know too , it shows the hd as one mass , no partitions

---

### Post by shreepads on 2012-10-12
> **eslam elbyaly said:**
> it is fat32 but i think the pc i've got has the kubuntu inside it or inside another partition. it was installed incorrectly . and i do not know if it is sda1/2/3, beside this , gparted does not know too , it shows the hd as one mass , no partitions

Run LiveCD and post output from

$ sudo parted -l

---

### Post by eslam elbyaly on 2012-10-14
> **shreepads said:**
> Run LiveCD and post output from

$ sudo parted -l
  fdisk -l , i do not know why , but i will try using the live usb or cd , and i will tell you what is going on .

---

