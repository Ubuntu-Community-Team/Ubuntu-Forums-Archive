---
title: "Hard Disks (One Missing)"
date: 2011-03-19
forum: General Help
---

### Post by hunterxaz on 2011-03-19
Hello,

I have Ubuntu 10.10 installed. My hard drives are as follows:

/dev/sda/ - 1500gb
1,2

/dev/sdc/ - 1000gb
1,2

/dev/sdd/ - 750gb
1

/dev/sdb/ - 500gb (main Windows install)
1

/dev/sde/ - 999gb
1

--

Now I can access all of them except the 500gb one. How can I explore it or mount it? Why would it not be listed in the "Computer" section, while the others are?

sudo fdisk -l shows them all. I just can't access (because I don't know how.)

Thanks

---

### Post by mikewhatever on 2011-03-19
You could try mounting it manually just to check that it does mount.
```
sudo mount /dev/sdb1 /mnt
ls /mnt

```

...to unmount:
```
sudo umount /dev/sdb1
```

---

### Post by dcstar on 2011-03-19
> **hunterxaz said:**
> Hello,

**I have Ubuntu 10.10 installed**. My hard drives are as follows:
.........
Now I can access all of them except the 500gb one. How can I explore it or mount it? Why would it not be listed in the "Computer" section, while the others are?

sudo fdisk -l shows them all. I just can't access (because I don't know how.)

Thanks

[LIST=1]
[*]Change your forum profile - 8.04
[*]Use the Disk Utility to check the disk's mount point.
[/LIST]

---

### Post by hunterxaz on 2011-03-19
> **mikewhatever said:**
> You could try mounting it manually just to check that it does mount.
```
sudo mount /dev/sdb1 /mnt
ls /mnt

```

...to unmount:
```
sudo umount /dev/sdb1
```

Trying this, yields a "Segmentation Fault" -- any idea? Google says it's like a memory access violation.

---

### Post by hunterxaz on 2011-03-19
> **dcstar said:**
> [LIST=1]
[*]Change your forum profile - 8.04
[*]Use the Disk Utility to check the disk's mount point.
[/LIST]

Greetings. Thanks, that was old! Updated my profile.

Under the Disk Utility, I see it listed on my SATA channel.

Usage says "-" whereas other disks show "Filesystem"

I can run the Benchmark on it, so there is no access issue I think. Any tips?

Edit:

The other volumes show buttons to "mount" etc. This drive does not.

---

### Post by hunterxaz on 2011-03-19
I should also note, that on this particular drive, the info area says "Unknown 490gb" and then a "Free 10gb" space. All other drives show 1.5gb NTFS, etc.

---

### Post by restorator on 2011-03-19
Is this a wubi install?

---

### Post by hunterxaz on 2011-03-19
Negative, booted up off the latest Ubuntu 10.10 CD.

I noticed an error when booting up:

```
udevd-work[115]: '/sbin/blkid -o udev -p /dev/sdb1' unexpected exit with status 0x000b
```

---

### Post by hunterxaz on 2011-03-19
Google is pretty unhelpful with that error code. Wondering if it's really a HD issue or a config issue. When I boot up with LiveCD, that disk is also non-auto mounted. Wonder if I try a different distro?

---

### Post by hunterxaz on 2011-03-20
Burning Mint Linux to check. Any ideas in the meantime?

---

### Post by hunterxaz on 2011-03-20
Don't have any DVDs to burn mint Linux on at the moment. Does anyone know of a smaller distro / live CD that I can use to check and see if it's available there?

Any ideas on that error code?

---

### Post by hunterxaz on 2011-03-20
On the Fedora live CD right now. I tried to do:

sudo mount /dev/sdb1 /mnt

and it says "liveuser is not in the sudoers file. This incident will be reported" 

So I su root and I am on that, I tried it again, and this time I get "Segmentation fault (core dumped)"

Any help? Obviously the disk has some issues with Linux. It works fine under Windows. (Not saying that's a good thing.)

Hmm!

---

### Post by hunterxaz on 2011-03-20
Must have been some bad data on the HD somehow. Wiped it and reinstalled Windows on it, then reinstalled Ubuntu on it alongside it, and everything is working just fine.

---

