---
title: "Hard disk full...."
date: 2012-04-22
forum: General Help
---

### Post by killerkyle113 on 2012-04-22
I am getting messages saying that there is not enough disk space left on the file system. When investigating i see that root is mounted on /dev/loop0 and not on the partition i had it installed on which is sda5.  Sda5 has ~100gb left on it so it should not be a problem. Any help on why root is mounted on dev/loop0 or help on how to transfer the whole file system over to sda5 and /or just remount it on there would be greatly appreciated. Thanks

---

### Post by TransitMan on 2012-04-22
> **killerkyle113 said:**
> I am getting messages saying that there is not enough disk space left on the file system. When investigating i see that root is mounted on /dev/loop0 and not on the partition i had it installed on which is sda5.  Sda5 has ~100gb left on it so it should not be a problem. Any help on why root is mounted on dev/loop0 or help on how to transfer the whole file system over to sda5 and /or just remount it on there would be greatly appreciated. Thanks

Your /dev/sda5 is formatted and dedicated to Linux Swap. There is no OS on /dev/sda5.

Near as I can tell, everything is on that /dev/loop0, whatever that is. From your screenshot it is not even listed in gparted.

You'll have to go back and re-install Linux again, and this time blow away /dev/sda5, and the one unallocated and format them as one /dev/sdax to ext4. Then re-install on the /dev/sda5 and you should be good to go, with approximately 104GB of useful disk space.

---

### Post by killerkyle113 on 2012-04-22
Isthere a way to find where the current file system is and just dd it over to sda5 and then go from there?

---

### Post by efflandt on 2012-04-22
Is this a Wubi installation (installed within Windows instead of Linux on its own partition)?  I have never done that, but I wonder if your Linux filesystem is actually a loop mounted Windows file.  Maybe the contents of /etc/fstab would give a clue where that loop mounted system is.

---

### Post by killerkyle113 on 2012-04-22
Also i found this interesting.. when i click properties of / ... it says there is 140.8tb of data.... there most certainly is not. and also the number of items is not stoping its up into the 800k now... also this was not a wubi install. i booted from live cd and could have swore i installed it on sda5 but... idk for certain. it was over a year ago and i have installed many linuxes on many machines seince then and have used wubi for some. 
fstab : ```

kyle@ubuntu:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

---

### Post by Paqman on 2012-04-22
> **killerkyle113 said:**
> also this was not a wubi install.

Actually, it is. There are a couple of giveaways:
[LIST=1]
[*]The presence of loopmounted devices
[*]A location listed as /host
[/LIST]

/host is your Windows NTFS partition, and is a location that only exists on Wubi systems.

One of the problems of Wubi is that it tends to be a bit stingy in allocating space when you install. Wubi installs often run out of space.

Best thing to do is have a good cleanout of junk on your system. To quickly create some space:
```
sudo apt-get clean
```
Then install [Bleachbit]("apt:bleachbit") and use it to clear out all your caches (system, browsers, thumbnails, etc) and free up some space.

---

