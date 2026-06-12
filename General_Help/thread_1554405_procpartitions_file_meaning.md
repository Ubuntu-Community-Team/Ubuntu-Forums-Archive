---
title: "/proc/partitions file meaning"
date: 2010-08-16
forum: General Help
---

### Post by aracky on 2010-08-16
hello,
my /proc/partitions file contains the following:

major minor  #blocks  name

   8        0  244198584 sda
   8        1  241223680 sda1
   8        2          1 sda2
   8        5    2972672 sda5


can anyone explain the meaning of this info?

thanks.

---

### Post by aracky on 2010-08-17
anyone?

---

### Post by john newbuntu on 2010-08-17
Well, the major number is 8 that indicates it to be a disk device. The minor ones are your partitions on the same device. 0 is your entire disk, 1 is your primary, 2 your extended and 5 your logical partition.  The rest is of course block size and name of disk/partition.

A "sudo fdisk -l" would have reinterpreted the same data in a slightly better way.

---

### Post by aracky on 2010-08-17
hi,
 
first of all thanks for the kind reply.
secondly, i didn't asked my question properly, since i know the info you gave me so i'll rephrase it:
how can i know what data is in the sda5? i think its for swapping but i'm not sure.
i indeed tried fdisk -l in advance but i get no answer. the man page for fdisk -l says that if i get no answer when typing it than i have the requested info in /proc/partitions.
 
 
any suggestions?

---

### Post by john newbuntu on 2010-08-17
Did you add the "sudo" to fdisk -l . I'd be surprised if you get no output.  Can you please post anything that you get after running that command?
Also, take a look at (system->admin->system monitor) and go to the filesystems tab and see if you can spot /dev/sda5 there.
Also try "sudo sfdisk -l /dev/sda".

To see if it is swap, try "swapon -s".  Check the swap entry listed in your /etc/fstab and compare it with the UUIDs available in "sudo blkid -c /dev/null".

As a final resort, fire up gparted and see if that gives you any information.

---

### Post by KeyserSoze93 on 2010-08-17
In a root shell (su - or sudo -s), try running:

```

for i in /dev/sda?; do

if (! fdisk -l|egrep "$i.*Extended"); then

mount $i /mnt &&
echo "$i:" &&
ls /mnt &&
umount /mnt

echo

fi

done


```

It will need fdisk to work, but, to be honest, if it doesn't then there is something very wrong with your system.

This will try and mount every normal (non-extended) partition, list what's on it, unmount it and move on to the next.

If it's a swap partition, mount will tell you that too.

Hope it helps...

---

### Post by ranch hand on 2010-08-17
Or you could fire up the live CD and take a look at your drive with gparted System>Administration>Gparted Partition Editor.

You could also install gparted on your OS.  I do not recommend this to you as you can do some major damage with it and I am not sure that you have the experience to avoid doing so.

The live CD is safe, just look, do not format anything.

---

### Post by aracky on 2010-08-17
thanks guys,

sudo fdisk -l did the trick.

have a good day...

---

