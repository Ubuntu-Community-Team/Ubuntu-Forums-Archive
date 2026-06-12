---
title: "ubuntu corrupting NTFS files and folders"
date: 2011-01-20
forum: General Help
---

### Post by snisarg on 2011-01-20
i am new to ubuntu, and frequently access most of my data which is currently in the NTFS partition.

i have observed that, at times while reading/writing information on the NTFS partition, ubuntu corrupts the data of the file/folder. This is a serious problem. One of the folders it corrupted couldnt even be deleted and i had to use windows chkdsk feature, which found a lot of problems in that folder, thus deleting the whole directory.

now once again, one of my file(program) got corrupted, and only has garbage in it.

How do i deal with this problem? Can i solve it, or should I just avoid using ubuntu with the NTFS partition?

---

### Post by snisarg on 2011-01-20
anyone?

---

### Post by srs5694 on 2011-01-20
Most people don't report this sort of problem, but if you're having it, you're having it.

My recommendation is to repartition your disk so that you keep your Windows boot files, programs, and Windows-only user files separate from files you want to share between Windows and Ubuntu. If the files you want to share never exceed 4 GiB in size, you can make the shared-data partition FAT rather than NTFS; this will use a different driver in Linux, which will probably avoid whatever bug is causing problems for you.

If you decide to repartition by resizing existing filesystems, be sure to back up first. Resizing partitions is inherently dangerous. Also, use Windows' own tools for resizing your Windows boot partition; Windows is very finicky about its boot partition, so it's best to do this job using Windows' own tools.

---

### Post by Mark Phelps on 2011-01-21
You didn't say if the partition getting corrupted is a Windows OS partition or a data partition, but if it is OS, you're fortunate that Windows has remained bootable all this time.

I try my best to advise folks to NOT write to Windows OS partitions via Linux distros.  While the results are generally OK, sometimes, as you have experienced, they are not.

The advice to have a separate data only partition is the best one, and it's one that I have used successfully.  At least that way, you can still boot into Windows and runk chkdsk when needed.

Also, if you're mounting with a filesystem type of "ntfs", changes that to "ntfs-3g".  That generally does a better job of handling NTFS filesystems.

---

### Post by snisarg on 2011-01-29
Thank you for your replies.

So i should avoid using NTFS folder altogether. Okay, I shifted the files i access frequently, and since then i have faced no problem.

It would really help if you can highlight how do i convert NTFS to NTFS-3g, if it does surely make access better/surer.

---

### Post by Morbius1 on 2011-01-29
In ubuntu ( and I think most other linux distros ) "ntfs" is "ntfs-3g". I suppose a better way of saying that is that there is a symlink to "ntfs-3g" from "ntfs".

---

### Post by theras2000 on 2011-03-23
Just for the record, I'm having the same problem.  I just installed Maverick Meerkat a week ago on my spare (3rd) partition.  Partition 1 is WinXP (NTFS) and partition 2 is my data (NTFS).  I really want to keep it NTFS for the security.  I thought it was due to my hibernating (in XP and Ubuntu) but even when I shutdown/reboot normally it happens.  This can be for brand new files that I create from Ubuntu, or existing XP files that I modify in Ubuntu.  It's really bugging me as I have important documents that I don't want to risk (and I've already had to recover some from backup because chkdsk just kills anything that Ubuntu has touched).

---

### Post by lithopsian on 2011-03-23
Post your /etc/fstab file to see how you are mounting the NTFS partition.  If you are not using the nfts-3g driver then you should probably switch to it.  You just need to install the package and change the mount.  The NTFS partition itself remains the same, NTFS, but Ubuntu will read and write it more safely and permissions will be handled better.

---

### Post by theras2000 on 2011-03-23
Thanks for the quick help! Here's the file below (pretty small so I just posted it). I can't see if it's ntfs-3g or not. I went to Synaptic Package Mgr and the 3 or so packages that I found under ntfs-3g all looked to be already installed as the only option was 'reinstall'. I'm off but will check back here tomorrow.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=74c0747b-89ed-4d0f-b898-af5e0231de50 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=61e5147f-3f05-4e29-a7bd-4ad7ea13699e none            swap    sw              0       0

---

