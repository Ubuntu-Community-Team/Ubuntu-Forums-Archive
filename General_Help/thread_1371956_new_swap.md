---
title: "new swap"
date: 2010-01-04
forum: General Help
---

### Post by swatc1h on 2010-01-04
hello ubuntu 1st time user. so i've installed without a swap and would like one. my specs run p8700, 2gb ram and 148gb. i need someone to pull out numbers for me, i suck in calculating this.

---

### Post by HermanAB on 2010-01-04
Read the 'swapon' man page.

---

### Post by garvinrick4 on 2010-01-04
Unless you run programs that are really RAM intensive I would not knock yourself out.
You most likely will never even need more than 2 gig. Use a program called System Monitor in your panels and you can see what you are using at any given time before screwing around with adding a swap partition. Just a personal opinion.

---

### Post by swatc1h on 2010-01-04
wanna do the four step process. is this correct and will this cmd make a swap within the same "/" partition. ```
sudo dd if=/dev/zero of=/mnt/2048Mb.swap bs=1M count=2048
```

---

### Post by swatc1h on 2010-01-04
don't want this thread beyond pages. so the above. and thank you.

---

### Post by cenzorrll on 2010-01-05
use gparted instead if you're new to linux, just stick in the cd or usb you used to install ubuntu, under system>administration there should be "partition editor" or "gparted"

open that and resize your ubuntu partition to leave something a little more than 2048 mb behind (2500 would do) and make a swap partition in the empty space.  click apply and wait till it's completely done.  make note of which device the swap is (/dev/sda2 or something like that)  then you can restart.

you'll probably also need to add it to your fstab.

to do this do:

```
gksu gedit /etc/fstab
```

then you'll see some stuff like:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=21a3b110-7a67-4635-bbd1-bdbfca26a24c /               ext4    errors=remount-ro 0       1
```

at the bottom add:

```
/dev/sdaX none            swap    sw              0       0
```

where X is the number for your swap partition

---

### Post by swatc1h on 2010-01-05
i've installed gparted but i can only format or view partitions. gonna check if usb drive will work.

---

### Post by cenzorrll on 2010-01-05
> **swatc1h said:**
> i've installed gparted but i can only format or view partitions. gonna check if usb drive will work.

that's because your partition is mounted, you won't be able to unmount the partition to do any changes. which is why you need the ubuntu live cd to do any changes to the root partition (also, make sure it is the ubuntu partition if you're dual booting, not windows or any other, it'll be either ext3 or ext4 depending on your version of ubuntu)

---

### Post by garvinrick4 on 2010-01-05
You sound pretty new to Linux, watch yourself with gparted!!!!!
Read this first.

[GParted partitioning software - Full tutorial]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by Sef on 2010-01-05
As for size, 1 gb swap will be more than enough.  If not, then get more ram.

---

### Post by cenzorrll on 2010-01-05
> **Sef said:**
> As for size, 1 gb swap will be more than enough.  If not, then get more ram.

i say over 2gb in case he/she wants to hibernate and somehow filled up their ram, having a laptop and losing battery power without enough swap isn't very fun if you're working on something.

---

### Post by swatc1h on 2010-01-05
i ended up with unallocated space like you said. but for some reason i can't linux swap it or anything, it's just as is.

```
unallocated-unallocated
/dev/sda1-ntfs-system reserved
/dev/sda2-ntfs-win7
/dev/sda3-ext4-ubuntu
unallocated-unallocated
/dev/sda4-ntfs-storage
```

---

### Post by swatc1h on 2010-01-05
goodmorning ubuntu.

---

### Post by cenzorrll on 2010-01-05
> **swatc1h said:**
> i ended up with unallocated space like you said. but for some reason i can't linux swap it or anything, it's just as is.

```
unallocated-unallocated
/dev/sda1-ntfs-system reserved
/dev/sda2-ntfs-win7
/dev/sda3-ext4-ubuntu
unallocated-unallocated
/dev/sda4-ntfs-storage
```

ah, you got yourself into a little pickle here, a hard drive can only have 4 logical partitions, after that one of those needs to be an extended partition that contains your other partitions.  it looks like if you're going to want swap you need to make an extended partition that would contain at least two of your present partitions.

i think the best way to do it would be to reinstall ubuntu entirely within the extended partition (so your partitions would look something like this:

```
unallocated-unallocated
/dev/sda1-ntfs-system reserved
/dev/sda2-ntfs-win7
/dev/sda3-extended
  /dev/sda5-ext4
  /dev/sda6-linuxswap
/dev/sda4-ntfs-storage
```

of course, swap isn't entirely necessary, 2gb of RAM should be plenty for any linux distribution unless you do something like virtualization, or need to hibernate (i rarely hibernate, i just have it just in case i'm working on something important and lose track of my battery level)

so, if you really do decide you need swap, i suggest just reinstalling ubuntu, it would probably take less time than it would to make a copy of your ubuntu partition and paste it in the extended.

you can use gparted to copy partitions and paste them, which you can try with the ubuntu partition if you absolutely don't want to reinstall (in which case you'll also have to fix grub to look at your new partition, hence reinstalling=easier)

as always make sure to backup anything important. and if you don't fully understand something, you're probably better off not doing it.

---

### Post by swatc1h on 2010-01-18
i went with yr route, worked nice. thanks again.

---

