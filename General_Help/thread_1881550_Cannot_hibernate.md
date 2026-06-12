---
title: "Cannot hibernate"
date: 2011-11-15
forum: General Help
---

### Post by nyxm on 2011-11-15
Hey guys. I used Wubi to install 11.10 64-bit, and the first few times I logged on, I was able to hibernate. I preformed an Update Check and installed 209 updates. Now I cannot find an option anywhere to hibernate. Help.

---

### Post by bcbc on 2011-11-15
> **nyxm said:**
> Hey guys. I used Wubi to install 11.10 64-bit, and the first few times I logged on, I was able to hibernate. I preformed an Update Check and installed 209 updates. Now I cannot find an option anywhere to hibernate. Help.

Wubi doesn't support hibernation. Only suspend.

The reason is that Ubuntu requires a swap partition to hibernate (with the built-in mechanism) and Wubi uses a virtual partition and a swap *file*.

---

### Post by nyxm on 2011-11-15
> **bcbc said:**
> Wubi doesn't support hibernation. Only suspend.

The reason is that Ubuntu requires a swap partition to hibernate (with the built-in mechanism) and Wubi uses a virtual partition and a swap *file*.

So then why was I able to hibernate at first until I installed updates? And are you sure that there is no swap? Because when I run "free -m" in terminal it outputs:

             total       used       free     shared    buffers     cached
Mem:          1745       1627        117          0        412        440
-/+ buffers/cache:        774        970
Swap:          255         45        210

It shows memory allocated for swap. Or is it just like a virtual swap partition inside of a virtual hard drive?

---

### Post by bcbc on 2011-11-16
It's a swap file. It works the same as a swap partition except you can't hibernate with it. Besides, you need a swap partition that is bigger than the size of your RAM to hibernate, and that swap file is only 255MB.

You can see it if you run:
cat /etc/fstab

it looks like this:
```
bcbc@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
bcbc@ubuntu:~$
```

And
```
bcbc@ubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
/host/ubuntu/disks/swap.disk            file		262140	0	-1
bcbc@ubuntu:~$ 

```

You can hibernate from a wubi with a swap partition, but you need to create a swap partition (and the whole point of wubi is not having to partition) e.g.
```
bcbc@ubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
/host/ubuntu/disks/swap.disk            file		262140	0	-1
[COLOR="Blue"]**/dev/sda7                               partition	5119996	0	-2**[/COLOR]
bcbc@ubuntu:~$ 

```

---

