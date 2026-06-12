---
title: "Parted CLI"
date: 2011-06-28
forum: General Help
---

### Post by bakegoodz on 2011-06-28
I'm trying to write a script, but I'm having a hard time with Parted's syntax. 

 What command would I use with Parted to create 1 partition that takes up the entire drive /dev/sda, if I have to choose a partition type ntfs is fine. Another tool like sfdisk would be fine if it can start the partition at the 1 MB position, so it is nicely optimized for Advanced Format (4k sector) and SSD drives. Big thanks to anyone that can help me with this!

It's a long story why I need this, please no answers that can't be scripted in the command line, Thanks again!

---

### Post by seawolf167 on 2011-06-28
What about something like this:

```
sudo mkfs -t ext3 /dev/sda
```

Read more:

```
man mkfs
```

---

### Post by srs5694 on 2011-06-29
I don't recommend creating a filesystem on a hard disk without a partition table. That's just too inflexible; if you want to change things in the future, the only option available is to back up, partition, and restore. There's also the risk that some disk utility will flake out when it sees a "raw" filesystem with no partition table on the disk, with unknown consequences.

In principle, the following will do it:

```
parted --script /dev/sdc mkpart primary ext3 2048s -0

```

Unfortunately, parted seems to treat the "-" in "-0" as an indication that "0" is an option rather than the end value. I'm not sure how to get around this problem. If you omit the "-0", parted will prompt you for an end value, and typing "-0" there does the trick.

It's possible to do this with either sfdisk or fdisk, but the only way I've figured out involve feeding fdisk input via input redirection. That's a bit awkward. There's probably a more elegant way to do it with sfdisk, but I've always found sfdisk's syntax awkward, too.

Does the disk have to be an MBR disk? If it can be a GPT disk, you could do it quite easily with sgdisk:

```
sgdisk -g -n 0:2048:0 /dev/sda

```

If you want to be sure the disk is completely empty, you'd use -o before -n:

```
sgdisk -g -o -n 1:2048:0 /dev/sda

```

You can add other options to change the partition type code, set a partition name, etc.

Actually, although it's inelegant to create GPT just to convert it to MBR, this will work:

```
sgdisk -g -o -n 1:2048:0 -m 1 /dev/sda
```

Note that all of these are highly dangerous, since they'll modify the disk without prompting. (The last two will wipe out any existing partitions, but the first will at least leave anything that was there before intact, although it'll convert it to GPT form.) Be sure the script does what it's supposed to do by double-checking input, displaying the partition table to the user, or whatever is appropriate to avoid disaster.

---

### Post by bakegoodz on 2011-07-19
I do want to create a partition table. I want to start the first and only partition 1 MB in, so all those new drives nicely align.

---

### Post by psusi on 2011-07-19
Use 0% and 100% as the start/end arguments to mkpart.

---

