---
title: "Bad Superblock...? I think..."
date: 2011-01-31
forum: General Help
---

### Post by Davez69gto on 2011-01-31
Hello Everyone,

Recently I purchased a Fantom Drives GreenDrive 2TB.  It's esata and usb2.  After I purchased it I connected it as esata and formatted it as FAT32 and moved a bunch of data over to it.  I added new data and every once in a while it would act up and make ubuntu hard to shutdown to the point that i had to hard shutdown.  This happened a few times and the best way to fix it was to connect it via usb, unmount it and everything worked just fine on the next boot.  

After a bit I found that I needed to change from FAT32 to EXT4 for permission reasons.  I moved all my data off, formatted and moved everything back on.  Sometimes during this move it would act up and not transfer.  After a reboot it usually worked as normal.  

A few days ago I was working on my other drives and for some reason this one unmounted.  After the unmount I couldn't get it to remount.  I got a message about how it was busy and might be being used by an application.  After that I figured something was wrong and did a little research.

I'm figuring that my superblock is bad.  

here are the things that I've found so far.  

While running "dmesg |tail" I got:
    [ 9415.813742] sd 2:0:0:0: [sda] READ CAPACITY(16) failed
    [ 9415.813748] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
    [ 9415.813755] sd 2:0:0:0: [sda] Sense not available.
    [ 9416.018043] sd 2:0:0:0: [sda] READ CAPACITY failed
    [ 9416.018049] sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
    [ 9416.018055] sd 2:0:0:0: [sda] Sense not available.
    [ 9416.126395] sd 2:0:0:0: [sda] Asking for cache data failed
    [ 9416.126402] sd 2:0:0:0: [sda] Assuming drive cache: write through
    [ 9416.126412] sda: detected capacity change from 2000398934016 to 0
    [23970.688527] EXT4-fs (sda1): unable to read superblock
    [24009.536174] EXT4-fs (sda1): unable to read superblock
    [25484.708610] EXT4-fs (sda1): unable to read superblock

When running "mke2fs -n /dev/sda1" i got:
    mke2fs 1.41.11 (14-Mar-2010)
    mke2fs: Permission denied while trying to determine filesystem size

When running "sudo mke2fs -n /dev/sda1" i got:
    mke2fs 1.41.11 (14-Mar-2010)
    Filesystem label=
    OS type: Linux
    Block size=4096 (log=2)
    Fragment size=4096 (log=2)
    Stride=0 blocks, Stripe width=0 blocks
    122101760 inodes, 488378637 blocks
    24418931 blocks (5.00%) reserved for the super user
    First data block=0
    Maximum filesystem blocks=0
    14905 block groups
    32768 blocks per group, 32768 fragments per group
    8192 inodes per group
    Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736,     1605632,      2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

When running "sudo fsck -b 32768 /dev/sda1"
    fsck from util-linux-ng 2.17.2
    e2fsck 1.41.11 (14-Mar-2010)
    fsck.ext2: Attempt to read block from filesystem resulted in 
        short read while trying to open /dev/sda1
    Could this be a zero-length partition?

I pretty much don't know what to do from here... I have about 800gb of data on there that I would like to keep.  I was thinking maybe there's a way to run the last command.  I dn.  I haven't dealt much with fs and such before.  

Any help would be appreciated.

---

### Post by Davez69gto on 2011-01-31
I figured it out.  I think I didn't have it properly unmounted because when I restarted with my esata cable connected and made sure that my fstab entry was commented out then ran the command e2fsck -f everything worked and I have all my data back!!!  

Thanks Everyone for looking.

---

### Post by srs5694 on 2011-01-31
Your error messages indicate a hardware failure. It's hard to say if this is in the drive itself, the interface circuitry in the case (but outside of the drive), the cabling, or even the interface circuitry in your computer. I'd investigate this further before storing more data on the drive.

---

