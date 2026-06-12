---
title: "Help my PC wont boot"
date: 2011-05-27
forum: General Help
---

### Post by ThatCoolGuy220 on 2011-05-27
ok i was having issues on my version of ubuntu so i decided to install it again but there wasnt enough space.

So i ran puppy for erase my partitions:

I did it via fdisk but i dindt created a new partition i just erased them silly of me:

Now when i boot i get

error: no such partition
Grub rescue >

---

### Post by ThatCoolGuy220 on 2011-05-27
Please help im stucked here

---

### Post by yetiman64 on 2011-05-27
> **ThatCoolGuy220 said:**
> ok i was having issues on my version of ubuntu so i decided to install it again but there wasnt enough space.

So i ran puppy for erase my partitions:

I did it via fdisk but i dindt created a new partition i just erased them silly of me:

Now when i boot i get

[B]error: no such partition
Grub rescue >[/B]

Even though you have deleted the partitions (including grubs boot files) the grub MBR code is still in the MBR and is now looking for a non existent partition for its files.

Reinstalling Ubuntu from a live cd or live USB will overwrite the grub boot code and should fix your situation.

If you need more space to install Ubuntu you can use gparted from the live cd / live USB to resize/create partitions first if needed.

Edit: MBR = master boot record, the first track of the boot drive.

---

### Post by yetiman64 on 2011-05-27
Sorry for double posting, it is important we know a couple of things,

1 Are you dual booting with Window ?

2 If so, is it a Wubi install inside Windows ?

---

### Post by ThatCoolGuy220 on 2011-05-27
lol bro i though there wasnt solution and no i havent used windows since april.

i was creating the live CD on an logical partition


I did live cd on a Primary one but cannot install natty narwhal.

it says i dont have enough space.

Though Gparted doesnt show my HDD

---

### Post by ThatCoolGuy220 on 2011-05-27
Im formating my HDD via puppy.....

Formated as FAT 32

now i will try install

---

### Post by yetiman64 on 2011-05-27
> **ThatCoolGuy220 said:**
> lol bro i though there wasnt solution and no i havent used windows since april.

i was creating the live CD on an logical partition


I did live cd on a Primary one but cannot install natty narwhal.

it says i dont have enough space.

Though Gparted doesnt show my HDD
Good to hear no Windows present especially Wubi install, the use of Puppy would have been a real nightmare for you. ;)

You should be able to install Ubuntu to a logical partition, even natty, all my linux partitions here are logical (including Natty). The only one not Logical is a dedicated Grub boot partition (not yet implemented). I allow for up to 6 Linux installs (12 partitions).

The "not enough space" error is because the installer needs "unallocated space" to install to iirc. If you use a live cd and prepare partitions for the new install you can use the manual installer (last in the list - I think it is referred to as "something else") and maually point /, swap and /home to there respective positions.

Good luck.

**Note Ubuntu WILL NOT install to FAT32 or NTFS.**

---

### Post by ThatCoolGuy220 on 2011-05-27
Thanks a lot Bro.

Now im enjoying my linux again.

---

