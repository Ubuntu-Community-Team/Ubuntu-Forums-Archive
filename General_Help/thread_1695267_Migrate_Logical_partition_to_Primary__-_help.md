---
title: "Migrate Logical partition to Primary  - help"
date: 2011-02-25
forum: General Help
---

### Post by hallb on 2011-02-25
I'm running Ubuntu 10.10

I have been running a dual boot system for a while now and I haven't logged onto the Windows side for quite a while.  I'm ready to whack it.

What I want to do is get rid of sda1, sda2, sda3 partitions(all Windows related) - migrate my Linux install(sda5) to a Primary partition, migrate the swap out of the extended partition, and then make everything else my "data"(ext4) partition...so basically go to 2 primary partitions and a swap.

I know how to ultimately get to my one big "data" partition, but the part I'm not so sure or comfortable with is whacking the current Primary partitions and migrating the Ubuntu install to the new primary partition.  

Can someone give me some direction???  Thanks in advance!


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        1926    15360000    7  HPFS/NTFS
/dev/sda3            1926        8453    52428800    7  HPFS/NTFS
/dev/sda4            8453       77826   557238273    5  Extended
/dev/sda5            8453       12369    31457280   83  Linux
/dev/sda6           12369       12761     3145728   82  Linux swap / Solaris
/dev/sda7           12761       32411   157835264    b  W95 FAT32
/dev/sda8           32411       77826   364796928   83  Linux

---

### Post by srs5694 on 2011-02-25
Don't get hung up on primary vs. logical partition assignments. Linux is happy using either type, and the advantages of converting from logical partitions to primary partitions are so tiny that they shouldn't factor into your decision-making process.

Given your current setup and desirable final setups, I recommend you proceed by either copying everything to a new disk or by backing up, repartitioning, and restoring. The reason is that a desirable final setup would likely involve three partitions: The Linux root (/) filesystem (currently about 30 GiB), a swap partition (currently about 3 GiB), and a Linux /home partition (currently about 350 GiB, if that's how you're using [noparse]/dev/sda8).[/noparse] Unfortunately, your current layout is such that you'll have to move the start of each and every one of your Linux partitions to get to this point. Depending on how much data you want to save from each partition, you might need to move one or two partitions' start points twice. Such operations are inherently risky, so I can't recommend you do this without backing up first, and once you've done that, it's likely to be faster to wipe everything and restore the backup than to do the partition moves and resizes necessary to get from where you are to where you want to go.

If you can't currently back up, then I recommend you go buy a new hard disk so that you can do so. You might consider getting a new internal disk with the intention of copying your current system to it (with a modified partition layout), booting from it, and using the old disk as a backup disk; or you can buy a disk to use as a backup disk, back up to it, wipe your current disk, and restore everything with modified partitions.

The details of how to proceed depend on how much data you want to preserve from each partition and what route you choose to take for backups. Post back with this information if you want more advice; there are too many options to cover them all in a speculative manner.

---

### Post by hallb on 2011-02-25
Thanks for the reply.

I guess I'm not really hung up on the extended vs. primary...but, I figured I couldn't just whack all of the windows partitions(b/c boot lives on one) and then extend those into one of the others b/c my system wouldn't boot, right?  Or can I just move my boot sector?

As for backing up, I can to an external drive(this is a laptop) w/out problem.  I don't care about saving anything on the Windows partitions(but the boot issue is there).  I prefer not to re-install Ubuntu(lots of tedious settings for gnome and cairo-dock) and I want to keep everything on large partition, but I can merge those down to 1 partition before I start all of this.  

So what's the best method of backup/restore w/out having to reinstall?  Boot to live-cd, tar to external drive, repartition and untar?  Currently my backup scenario is that the install is expendable and all of my critical data goes up to Jungle Disk.

Thanks again for the help.

---

### Post by oldfred on 2011-02-25
If the install is expendable, why not a new clean install. /home has all your user settings, so you would not have to recreate them. Depending on if you currently have a separate /home just use that for the new install or copy all the files (including hidden files). Be sure to preserve ownership and permissions. Use same user id.

If you did make some system wide manual settings they would be in /etc, generally I do not copy /etc files back as a new (updated) version may have different settings.

You can then dual boot new and old versions until you are sure new version has all the configuration you like. 

If you used gparted to copy your current install you will have to reinstall grub2 and edit fstab. Not sure what else may change, but it should work, its just I prefer a clean instal as I know that will work as it is designed to.

---

### Post by srs5694 on 2011-02-25
A fresh install of the OS, while preserving /home, as oldfred suggests, may be the easiest way to go:


[list=1]
[*]Use tar, rsync, CloneZilla, or whatever software you prefer to back up your user data to an external hard disk. Be sure to copy everything in /home/yourusername, as well as any files you might be storing elsewhere.
[*]Unmount and disconnect the external hard disk.
[*]Boot the Ubuntu installer.
[*]When asked, tell it you want to partition manually.
[*]Delete all your old partitions and create new partitions for the Linux root (/), swap, and /home partitions.
[*]Install normally.
[*]Boot the new installation and use your preferred backup software to restore the backups you made earlier.
[/list]


If you don't want to re-install, you can do something similar, but it's a little trickier and more likely to present challenges when you go to boot the recovered system:


[list=1]
[*]Use tar, rsync, CloneZilla, or whatever software you prefer to back  up your entire installation to an external hard disk (minus your Windows partitions).
[*]Unmount and disconnect the external hard disk.
[*]Boot the Ubuntu installer into "try it now" mode (or whatever it's called).
[*]Use GParted (or whatever other partitioning software you prefer) to delete your existing partitions and create new ones in their place.
[*]Mount your new partitions at some convenient point, being sure to mount them in their correct relative positions -- for instance, mount the new root (/) partition at /mnt and the new /home partition at /mnt/home. (For some partitioning tools, such as CloneZilla, you should skip this step.)
[*]Attach your external hard disk and mount its partition(s)
[*]Restore your backups to the new partitions.
[*]Unmount and disconnect your external hard disk.
[*]Re-install GRUB. Unfortunately, I don't recall the exact command to do this from the Ubuntu install disc. If you can't find this information quickly, you could download [Super GRUB 2 Disk](http://www.supergrubdisk.org), use it to boot the computer, and then type "sudo grub-install /dev/sda" in a Terminal window.
[/list]


Choice of backup software is highly personal. A lot of newbies seem to like CloneZilla, but I'm not very experienced with it, so I can't offer much advice on its use. I've used tar for this sort of thing for close to 20 years, but it's not very newbie-friendly. You'd back up like this:

```

cd /
sudo tar cvzf /media/backups/backup.tgz --one-file-system / /home

```

This creates a backup in /media/backups/backup.tar (your external disk would be mounted at /media/backups; change that detail as necessary) of the root (/) and /home partitions. If you only want to back up /home, you'd change the end of this command to omit the " / ", leaving only "/home".

The restore would be something similar:

```

cd /mnt
tar xvzf /media/backups/backup.tgz

```

This extracts everything from /media/backups/backup.tgz into the partition(s) mounted at /mnt. There's no need for the "--one-file-system" option or to specify the directory/ies to be extracted; you want to get everything out of the tarball. The assumption here is that you've booted using an emergency disc and mounted the new root (/) at /mnt. If you only back up /home, you can boot normally, cd to /, and extract the tarball; or you can boot using an emergency disc, mount /home at /mnt/home, and issue the above commands.

---

### Post by srs5694 on 2011-02-26
I realized that I forgot something in my second procedure (for the complete backup and restore): You must adjust UUIDs so that the system will boot from the new partitions. There are at least three ways to do this:


[list]
[*]Some backup/restore tools will copy the UUIDs automatically. The "dd" utility will do this, for instance. CloneZilla might, but I'm not positive of that.
[*]After copying everything back to the original drive, you can edit the /mnt/etc/fstab and /mnt/boot/grub/grub.cfg files to change the UUID values for the new system. Alternatively, you can change the UUID references to numbered device references; however, this approach is more likely to break if you add disks or repartition your hard disk.
[*]You can use tune2fs to set the new filesystems' UUIDs to match those of the originals. Specifically, the -U option to tune2fs does this, as in "tune2fs -U 580d3322-2ff8-4692-a964-be996c2e9929 /dev/sda1". For swap space, you'd use mkswap and its -U option, as in "mkswap -U 90dfc155-fd37-4e73-a112-472ce434096c /dev/sda5".
[/list]


You can learn what UUIDs a filesystem or swap space uses with blkid, as in "sudo blkid /dev/sda1". You can use this *before* deleting the old filesystems if you want to leave /etc/fstab and /boot/grub/grub.cfg alone; copy the output to a text file, then cut-and-paste these values into the tune2fs or mkswap commands after you've created the new partitions. If you edit the /etc/fstab and /boot/grub/grub.cfg files, you'd use blkid to find the UUID values of the new filesystems and swap space, rather than the old ones.

---

