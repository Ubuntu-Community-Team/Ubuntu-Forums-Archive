---
title: "/boot too full to upgrade kernel"
date: 2010-12-26
forum: General Help
---

### Post by wgato on 2010-12-26
my /boot partition is full(ish) (on a dual boot laptop without a cd drive)
resizing my partitions is not currently in the cards
so i was wondering if i could remove anything from there without screwing up my system.
or maybe move something and make a link or something?

thanks

---

### Post by noah++ on 2010-12-26
A couple possibilities:
1. Delete (or move) the old kernel images from **/boot**.
2. Move **/boot** to the **/** filesystem

---

### Post by bodhi.zazen on 2010-12-26
> **noah++ said:**
> A couple possibilities:
1. Delete (or move) the old kernel images from **/boot**.
2. Move **/boot** to the **/** filesystem

No, do not delete old kernels, remove them with apt-get, synaptic, or what have you (depends on what OS or other OS you have installed).

---

### Post by wgato on 2010-12-26
which can i safely i remove?

System.map-2-6.29.4
config-2.6.29.4
grub
initrd.img-2.6.29.4
lost+found
memtest86+.bin
tmp
vmlinuz-2.6.29.4

the tmp directory has a number of things in it but i dont know how to tell what wreck the system and would be ok to delete.

the other OS i have on the machine is XP.

---

### Post by bodhi.zazen on 2010-12-27
> **wgato said:**
> which can i safely i remove?

System.map-2-6.29.4
config-2.6.29.4
grub
initrd.img-2.6.29.4
lost+found
memtest86+.bin
tmp
vmlinuz-2.6.29.4

the tmp directory has a number of things in it but i dont know how to tell what wreck the system and would be ok to delete.

the other OS i have on the machine is XP.

What is in /boot/tmp ? You can almost certainly delete that.

---

### Post by wgato on 2010-12-27
the name tmp does imply i can delete it but i just wasnt sure and didnt want to have an unbootable machine.

in tmp:
bin
bootsplash
conf
etc
init
initrd
lib
sbin
scripts
var

everything but bootsplash and initrd are directories and initrd is 32M.

---

### Post by bodhi.zazen on 2010-12-27
> **wgato said:**
> the name tmp does imply i can delete it but i just wasnt sure and didnt want to have an unbootable machine.

in tmp:
bin
bootsplash
conf
etc
init
initrd
lib
sbin
scripts
var

everything but bootsplash and initrd are directories and initrd is 32M.

Well "tmp" usually implies temporary and so it is easy to give the impression it is not needed.

Why are you keeping that stuff in /boot ? can you not back it up or store it elsewhere ?

---

### Post by wgato on 2010-12-27
i wasnt really using it for storage space or anything.  i never looked at it until now when i got errors about it being too full to install the upgrade.  i dont know the system well enough to know what damage deleting or moving things from /boot might do.
but i'll wipe out the tmp directory and maybe more when i restart this project tomorrow.  thanks for the help and confirming that these arent required files.

---

### Post by dcstar on 2010-12-27
Why do people stuff around with the standard partitioning?

The only - **ONLY** - change to the standard partition layout that makes any sense is having a separate /home partition - all else invariably leads to issues like this which wipe out any "benefit" that is somehow gained by doing these things in the first place.

---

### Post by noah++ on 2010-12-27
[accidental duplicate]

---

### Post by gsgleason on 2010-12-27
@dcstar: that's not necessarily true.

wgato: please show the output of 'df -h'

I have 4 kernels installed and my /boot directory is 93M.  How small is your /boot ?

---

### Post by noah++ on 2010-12-27
Some people like a separate **/boot** partition for security. They'll only mount it when actively working with it.

It may not be the case anymore, but I think it has also been necessary to use a separate **/boot** if your **/** filesystem were in some newer format GRUB couldn't read.

I can also think of field cases where some part of the system had radically different roles from others. In one instance, while much content would be added to and deleted from a server, **/var **in particular was important but never grew much, so got its own small partition. It was even stored on different disk technology, sometimes.

As in my case, it is absolutely necessary to have a separate **/boot** partition when LUKS encrypts **/**.

---

### Post by bodhi.zazen on 2010-12-27
> **dcstar said:**
> Why do people stuff around with the standard partitioning?

The only - **ONLY** - change to the standard partition layout that makes any sense is having a separate /home partition - all else invariably leads to issues like this which wipe out any "benefit" that is somehow gained by doing these things in the first place.

That is far from true, but you do need to understand what you are doing.

As has been pointed out you may well need a separate /boot for LVM an LUKS as well as brtfs.

Separating other partitions can also increase security.

---

