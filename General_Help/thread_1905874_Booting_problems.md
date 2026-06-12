---
title: "Booting problems"
date: 2012-01-07
forum: General Help
---

### Post by shaymin on 2012-01-07
I have had problems booting:

[http://paste.ubuntu.com/796634/](http://paste.ubuntu.com/796634/)

when I try logging in, the computer tells me 

Error: File not found
Error: You need to load the kernel first

I have tried boot-repair, but it hasn't been working. any thoughts?

---

### Post by drs305 on 2012-01-07
I don't see any obvious errors in your RESULTS.txt file. Have you tried booting a different kernel?

You could also try booting from the grub terminal (press 'c' at the menu) with the following:

```

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

---

### Post by shaymin on 2012-01-07
thanks for the suggestions. Unfortunately, I tried booting from different kernels (from recovery mode and also from normal mode) and still couldn't get a successful boot.

I tried your grub terminal commands, but when I enter
```
initrd /initrd.img

```

the terminal says something to the effect of "can't read file."

---

### Post by shaymin on 2012-01-08
Bump

---

### Post by drs305 on 2012-01-08
Since you are getting an error on the initrd line, either the shortcut 'initrd.img' may be the problem or the actual initrd.img file may be corrupt. However, if none of the kernels work the problem is more likely something more universal.

It is possible the partition has an error. You can try to fix this by running an fsck check. This  must be done with the partition unmounted, so you would need to boot the LiveCD to the Desktop, open a terminal, and then run the following commands:
```

sudo e2fsck -fyv /dev/sda1
```

---

### Post by shaymin on 2012-01-08
Here is what I get:

```
ubuntu@ubuntu:~$ sudo e2fsck -fyv /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  350679 inodes used (4.55%)
    1089 non-contiguous files (0.3%)
     271 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 327946/95/1
 3412825 blocks used (11.10%)
       0 bad blocks
       1 large file

  291117 regular files
   30251 directories
      59 character device files
      26 block device files
       0 fifos
     513 links
   29212 symbolic links (22537 fast symbolic links)
       5 sockets
--------
  351183 files

```

So I forgot to mention, my computer was working fine until I shut off the computer when knotify4 was consuming a large amount of RAM (~1 GB). I did not encounter these problems until then.

---

