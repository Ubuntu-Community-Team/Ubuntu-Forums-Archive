---
title: "Fix &quot;Bad Sectors&quot; on my HDD?"
date: 2010-02-25
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-25
I have been experiencing ongoing system freezes. I am led to believe that it MAY have something to do with "Bad Sectors" on my Hard Drive. I am currently using the Live CD because even when I re-install it on my hard drive either it randomly stop booting or it freezes after 2-10 minutes of usage. If there is a way to repair "Bad Sectors" I am definitely willing to give it a shot. I know this isn't very good hardware but it used to do the job... The hard drive is a Hitachi DK23EA-30 30GB. Any ideas? I'm willing to do anything to get my laptop running again. UNFORTUNATELY I am unable to obtain a new Hard Disk. Any help would be greatly appreciated.
Regards, 
CharlesJWelsh

EDIT: And when I am on the "Live Disk" I do not have the freezing issue so I am pretty sure it is not regarding my laptop overheating. Or the visual effects. I know it is not a "Kernal Panic". (Caps Lock key doesn't flash nor does my laptop express any other symptoms of a "Kernal Panic" (I experienced them in Wubi back when I had Windows installed on my Laptop.))

---

### Post by Johnny B on 2010-02-25
unmount the drive and run

where XXX is your hdd:
> sudo fsck /dev/XXX 




<if you are using ext4 consider using ext3 next time, it seems more stable>

---

### Post by CharlesJWelsh on 2010-02-25
When I go to format my HDD and re-install ubuntu it randomly freezes. The disk worked fine on my mothers laptop. No freezing... Her Ubuntu is running fine. So I know it has nothing to do with my Installation Disk as well.

---

### Post by CharlesJWelsh on 2010-02-25
Is this what you are looking for?


fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/XXX

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by CharlesJWelsh on 2010-02-25
I'm sorry could you elaborate on the "ext3" and "ext4" thing and how I would do that?
I am still new at this...

---

### Post by Johnny B on 2010-02-25
this is how you fix bad sectors on your hard drive, but it probably wont help if you are running the live cd and it randomly freezes.

you need to replace XXX with whatever your hard drive is at, typically hda1 or sda1

---

### Post by CharlesJWelsh on 2010-02-25
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 150808/1756512 files, 811063/7012352 blocks

---

### Post by MooPi on 2010-02-25
You may want to force the check even though it came back clean. With the previous errors it seems practical.  ```
sudo e2fsck -n -f /dev/sda1
```

---

### Post by CharlesJWelsh on 2010-02-25
Screenshot of the HDD info. IDK if it's going to be of any use...

@MooPi
Here are the results...


ubuntu@ubuntu:~$ sudo e2fsck -n -f /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 150808/1756512 files (0.2% non-contiguous), 811063/7012352 blocks

---

### Post by Johnny B on 2010-02-25
it should say "Checking inodes, blocks, and sizes"
make sure its unmounted and try adding the -f option:
> sudo fsck -f /dev/sda1\



edit: nvm, too slow :)

---

### Post by CharlesJWelsh on 2010-02-25
Heres that output...

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1 
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 150808/1756512 files (0.2% non-contiguous), 811063/7012352 blocks

---

### Post by aarons6 on 2010-02-26
if you think the drive is going bad, unmount it, or boot with a live cd and run
sudo badblocks -svn /dev/sda
this will scan every sector and report its read ability..
if the drive is blank replace n with w and it will check its write ability.. (THIS WILL DELETE THE WHOLE DRIVE!!)

you can also install and run palimpsest
install these packages
libgdu-gtk0
libgdu0_0.3
libsqlite3
libatasmart0_0.13
devicekit-disks_004
gnome-disk-utility_0.3

this will tell you your drives S.M.A.R.T. status.

---

### Post by |{urse on 2010-02-26
If you nab a copy of Hiren's boot cd theres a great program on it called hdd regenerator.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

This works great if fsck2 fails you.

---

### Post by MooPi on 2010-02-26
I think you should prepare yourself for disk failure. Doesn't look good from the disk utility. One last attempt to fix would be good though. Boot the live CD once more and this time ```
sudo e2fsck -p /dev/sda1
```Good luck and I hope you can clean it up.

---

### Post by Tripletaco on 2010-04-18
How long does a "sudo fsck -f /dev/sda1" take?

---

