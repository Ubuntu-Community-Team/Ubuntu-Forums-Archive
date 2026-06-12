---
title: "mount error at boot"
date: 2012-06-21
forum: General Help
---

### Post by sulyi on 2012-06-21
I was having problems while moving my windows partition to a bigger one,  when I booted from the install CD and committed ```
 fixmbr 
```Grub died, but I could save it with a Live CD, but now my kubuntu boot with this error:

```
38.629607] EXT3-fs (sda1): error: couldn't mount because of unsupported optional features (240)
[   38.682282] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

```Then it boot correctly, but

```
$ ls /dev/disk
by-id  by-path

```There should be a by-uuid directory too.

And blkid or sudo blkid has no out put.

Please, help me.

---

### Post by sulyi on 2012-06-21
Now, first I've managed to make bios "see" two hdd, then I realised that the other one has a uuid.

Then I tied tune2fs witch did show the correct uuid.

But then:
```
$ sudo blkid -p /dev/sda1
/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
$ sudo  wipefs -n /dev/sda1
offset               type
----------------------------------------------------------------
0x438                ext4   [filesystem]
                     LABEL: Linux
                     UUID:  85969035-5d30-4415-8a44-338077cff006

0x36                 vfat   [filesystem]

$ sudo  wipefs -o 0x36 /dev/sda1
8 bytes were erased at offset 0x36 (vfat)
they were: 46 41 54 31 32 20 20 20
$ sudo  wipefs -n /dev/sda1
offset               type
----------------------------------------------------------------
0x438                ext4   [filesystem]
                     LABEL: Linux
                     UUID:  85969035-5d30-4415-8a44-338077cff006

0x0                  vfat   [filesystem]

$ sudo  wipefs -o 0x0 /dev/sda1
1 bytes were erased at offset 0x0 (vfat)
they were: eb
$ sudo  wipefs -n /dev/sda1
offset               type
----------------------------------------------------------------
0x438                ext4   [filesystem]
                     LABEL: Linux
                     UUID:  85969035-5d30-4415-8a44-338077cff006

0x1fe                vfat   [filesystem]

$ sudo  wipefs -o 0x1fe /dev/sda1
2 bytes were erased at offset 0x1fe (vfat)
they were: 55 aa
$ sudo  wipefs -n /dev/sda1
offset               type
----------------------------------------------------------------
0x438                ext4   [filesystem]
                     LABEL: Linux
                     UUID:  85969035-5d30-4415-8a44-338077cff006


```Now, I'll reboot, fingers crossed.

---

### Post by sulyi on 2012-06-21
Winner, winner, chicken dinner!
```
$ blkid 
/dev/sda1: LABEL="Linux" UUID="85969035-5d30-4415-8a44-338077cff006" TYPE="ext4" 
/dev/sdb1: UUID="66404023403FF7FF" TYPE="ntfs" 
/dev/sdb5: UUID="603cd86b-246b-43fe-a66e-7a86d0aa37c4" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="ba1ca8d8-81c2-4115-8e21-8f2324f496f1" TYPE="swap"
```

Yet,  sdb1 does not boot.

---

### Post by ben aveling on 2012-06-24
You are trying to boot Windows from grub?  If so, are you using the command line or GUI?

---

### Post by sulyi on 2012-07-26
Yeah, I had some problems getting windows and grub together. But, no I did not use the grub console, I've used a Live CD.  The problem was that windows fixmbr rewrote my Linux partition's boot record. 

In the end I couldn't find out, how to clone/move a windows partition, but at least It didn't go worst,  and ruined my Linux.

---

