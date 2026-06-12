---
title: "Cannot auto mount 2nd FakeRAID drive at boot  help"
date: 2011-06-18
forum: General Help
---

### Post by chipppy on 2011-06-18
Good Morning

I have a full working Mythbuntu 11.04 on a FakeRAID system (via ICH10R chipset).  The OS is sitting on a 250GB partition and working fine.
I am trying to get the 7.07TB partition mounted so that I can use it to store all my movies.

When I mount it via the [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") all works fine.
When I reboot it cannot mount due to device being not ready or unavailable

It appears the superblock goes missing at reboot.
I have it formatted to ext4 with a GPT partition table.

If I reformat and remount then all works fine again until I reboot.

Some info from termnal command that I found that might help
> main@FandBEnd:~$ e2label /dev/mapper/isw_dgiebjjgce_MytTV_Storage1
e2label: No such file or directory while trying to open /dev/mapper/isw_dgiebjjgce_MytTV_Storage1
Couldn't find valid filesystem superblock.
main@FandBEnd:~$ dumpe2fs /dev/mapper/isw_dgiebjjgce_MytTV_Storage1
dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs: No such file or directory while trying to open /dev/mapper/isw_dgiebjjgce_MytTV_Storage1
Couldn't find valid filesystem superblock.
main@FandBEnd:~$ 


My fstab file incase I have done something silly in there when writing the mounting code
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_dgiebjjgce_MythTV-OS1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_dgiebjjgce_MythTV-OS5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/mapper/isw_dgiebjjgce_MythTV-Storage1	/mnt/MythtvStorage	ext4	defaults	0	2

Anyone got any ideas on how to fix this so that my storage stay working at reboot?

Cheers
Chippppy

---

### Post by chipppy on 2011-06-21
BUMP

anyone got any ideas of how to fix missing super block auto mounting at boot issue pls

Cheers
chipppy

---

### Post by chipppy on 2011-07-06
BUMP

anyone please???????

Cheers
chipppy

---

### Post by chipppy on 2011-07-09
anyone?

---

### Post by stochastic79 on 2012-04-17
I have recently encountered a very similar problem, i.e. bad superblock errors on fakeraid after reboot.

I was able to get the drive to mount by checking the 'raid' flag in gparted.

I started a new thread on it here: [http://ubuntuforums.org/showthread.php?t=1959706](http://ubuntuforums.org/showthread.php?t=1959706)

---

