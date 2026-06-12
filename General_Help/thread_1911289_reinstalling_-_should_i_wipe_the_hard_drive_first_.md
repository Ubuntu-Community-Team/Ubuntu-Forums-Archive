---
title: "reinstalling - should i wipe the hard drive first?? and a question about partitions"
date: 2012-01-18
forum: General Help
---

### Post by over_my_head on 2012-01-18
OK, well, i've been having a couple of problems with my install of Ubuntu 11.10 - i'm pretty sure it was my fault and now that i've backed up my files, i'm really tempted to just start over from scratch with a new install.

is there anything to be gained by wiping the hard drive before reinstalling? i'm not worried about security since i'll still be the one using the laptop, i just dont want to have any lingering errors mess up the new installation.

also disk utility says i have three partitions on my hard drive: the primary partition, an extended partition and a swap partition.

i was dual booting with an old version of Ubuntu (8.10) before i switched completely to 11.10 and being rather clueless about disk partitioning, i'm not sure if I still need all three partitions. do I?

thanks in advance!

---

### Post by carl4926 on 2012-01-18
Why not
Clean things up

FYI: An extended partition is considered as a Primary but actually it's just a container for logical partitions.

Typically I do

swap = to RAM
/ (root) ext4 20 GB
/home ext4 (all the remaining space)

On bigger HD's I sort of mentally carve it 2, so as to have One install in use, and one as a backup and for the next release. So it looks like

swap
/ ext4
/ ext4
Extended
/home ext4
/home ext4

---

### Post by over_my_head on 2012-01-18
Ok. cool.
so if i run a command like: 
```

dd if=/dev/zero of=/dev/sda

```

(while booting from the CD)

once it's done I can just install from a CD or do i need to do anything special to set-up the hard drive for the install?

---

### Post by carl4926 on 2012-01-18
Any Ubuntu Live CD has Gparted

Just use that and create a new partition table
It will delete everything
Create your Partitions in GParted

Then reboot and run the installer

---

### Post by carl4926 on 2012-01-18
Here. I did a bit of a video for you.
It shows delete existing partition table by 'Create Partition Table'

Create simple
swap
/
/home

And then a multi boot layout as I suggested earlier
swap
/ ext4
/ ext4
Extended
/home ext4
/home ext4 	

[http://dl.dropbox.com/u/10573557/single_multi_linux_partit.mkv](http://dl.dropbox.com/u/10573557/single_multi_linux_partit.mkv)

*Remember these partitions are small and just represent a demo of the method.

---

### Post by over_my_head on 2012-01-19
hey thanks!

:-)

---

