---
title: "System says disk damaged on every boot, but fsck(8) says nothing."
date: 2012-04-13
forum: General Help
---

### Post by aps2012 on 2012-04-13
Hi all,

I wondered if anyone knows what the reason for this strange situation might be.

Running 10.10 and every boot I get a message saying something along the lines that "Serious damage was found on the disk mounted from /mnt/<path>". I always opt to continue and the system boots fine and there are operational problems.

Looking at syslog on one occasion I see:

```

Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.552927] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.552930] EXT4-fs (sda4): write access will be enabled during recovery
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898035] EXT4-fs (sda4): orphan cleanup on readonly fs
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898041] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670046
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898060] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670045
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898065] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670044
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898070] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670043
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898074] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670037
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898079] EXT4-fs (sda4): 5 orphan inodes deleted
Apr 12 17:33:54 ubuntu-pegasus kernel: [    9.898080] EXT4-fs (sda4): recovery complete
Apr 12 17:33:54 ubuntu-pegasus kernel: [   10.142589] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
Apr 12 17:33:54 ubuntu-pegasus kernel: [   19.569660] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro

```So, the system was complaining about **/dev/sda4**, which is actually my boot partition. [FONT=Courier New][SIZE=2]fsck[/SIZE][/FONT] says it was a read-only file system (strange for a boot partition), however it appears to have remounted it read/write to fix the errors.

Not entirely convinced about the state of my disk, I burnt the desktop version of the 11.10 CD and booted LiveCD mode, mounted my boot disk and ran [FONT=Courier New][SIZE=2]fsck[/SIZE][/FONT] manually, which unsurprisingly said this:

```

$ sudo fsck -v -n -C -f /dev/sda4
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  228363 inodes used (2.03%)
     143 non-contiguous files (0.1%)
     282 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 199059/64
 1791776 blocks used (3.99%)
       0 bad blocks
       1 large file

  163283 regular files
   29308 directories
      55 character device files
      25 block device files
       0 fifos
     539 links
   35619 symbolic links (29086 fast symbolic links)
      64 sockets
--------
  228893 files

```i.e., no errors. Nothing surprising there. However, the next boot I did I was surprised when I got the same message on the splash screen and on examining [FONT=Courier New][SIZE=2]syslog[/SIZE][/FONT] again found:

```

Apr 12 18:09:41 ubuntu-pegasus kernel: [    8.763760] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
Apr 12 18:09:41 ubuntu-pegasus kernel: [    8.763762] EXT4-fs (sda4): write access will be enabled during recovery
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457010] EXT4-fs (sda4): orphan cleanup on readonly fs
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457016] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670046
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457036] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670045
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457041] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670044
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457045] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670043
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457049] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 3670037
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457053] EXT4-fs (sda4): 5 orphan inodes deleted
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.457055] EXT4-fs (sda4): recovery complete
Apr 12 18:09:41 ubuntu-pegasus kernel: [    9.586241] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
Apr 12 18:09:41 ubuntu-pegasus kernel: [   19.068801] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro

```Note the i-nodes in the trace: they're **identical** to the ones in the previous trace that were supposedly fixed. The system was booted and shutdown in a normal and proper fashion in both cases.

Does anybody know what is going on here? How is it that every boot my system complains about "serious damage" with the same i-nodes and seems to be performing a fix of the same broken i-nodes, yet the i-nodes keep getting "re-broken" every time I shutdown?

Any ideas welcome.

Thanks in advance,

---

### Post by dcstar on 2012-04-13
> **aps2012 said:**
> 
........
So, the system was complaining about **/dev/sda4**, which is actually my boot partition. fsck says it was a read-only file system (strange for a boot partition), however it appears to have remounted it read/write to fix the errors.
........

**Never, ever** assume that the sda numbers from booting different environments are the same.

---

### Post by aps2012 on 2012-04-15
Hi dcstar,

Thanks for reply. Actually, I **never** assume anything, which is why I check that in addition to having the name */dev/sda4* I confirmed that the **UUID** on the disk and the **size** (all three of my partitions have different sizes) were exactly as expected before deducing which partition I was looking at.

11.10 being fundamentally the same OS as 10.10, in this case they both came to the same decision to name the disk that was causing problems as */dev/sda4*.

I look forward to any other suggestions you may have.

Thanks in advance,

---

### Post by dcstar on 2012-04-16
> **aps2012 said:**
> 
.........
I look forward to any other suggestions you may have.

Thanks in advance,

Find out why that filesystem is not being unmounted cleanly when you shutdown.

---

### Post by aps2012 on 2012-04-20
I've monitored the system for a few days during reboots and restarts and I can say categorically that there are no write errors to the device [FONT=Courier New][SIZE=2]/dev/sda4[/SIZE][/FONT] during shutdown.

However, I have pinned down some of the cause to an error in my [FONT=Courier New][SIZE=2]/etc/fstab[/SIZE][/FONT]. Simply speaking, my current disk configuration is like so:

```

Directory               | Mount Comments
============================================================
/                       ("hard" mount => /dev/sda4)
/mnt/home-areas         ("hard" mount => /dev/sda3)
/export/home-areas      ("bind" mount => /mnt/home-areas)

```User accounts are maintained on a separate partition from the system partition. In addition, user accounts are accessible via NFS ([FONT=Courier New][SIZE=2]/export[/SIZE][/FONT] is an NFS-managed export root) so a "bind" mount is used to connect the home-accounts directory in the NFS export area to the actual mounted drive.

Originally, my [FONT=Courier New][SIZE=2]/etc/fstab[/SIZE][/FONT] looked like this:

```

# / was on /dev/sda4 during installation
/dev/sda4        /                   ext4  errors=remount-ro  0  1

# local public home area(s) on /dev/sda3
/dev/sda3        /mnt/home-areas     ext4  defaults,errors=remount-ro  0  2

# directories exported via NFS
/mnt/home-areas  /export/home-areas  none  bind  0  0

```The problem with this setup is that I wanted to be able to unmount and remount [FONT=Courier New][SIZE=2]/mnt/home-areas[/SIZE][/FONT] freely while NFS was running. However, as the filesystem for a bind mount (where the target directory is *itself* a mount point) is cached at the time the bind is performed, it appears that the target directory underneath a bind mount can appear or disappear and the person accessing the mount won't notice as nothing as the directory cache for the bind point itself never gets updated.

I then changed [FONT=Courier New][SIZE=2]/etc/fstab[/SIZE][/FONT] to the following to try and get around this problem:

```

# / was on /dev/sda4 during installation
/dev/sda4       /                   ext4  errors=remount-ro  0  1

# local public home area(s) on /dev/sda3
/dev/sda3       /mnt/home-areas     ext4  defaults,errors=remount-ro  0  2

# directories exported via NFS
/dev/sda3       /export/home-areas  ext4  defaults,errors=remount-ro  0  0

```I now realise that it was at this point that the errors started. However, the errors were on [FONT=Courier New][SIZE=2]/dev/sda4[/SIZE][/FONT] regarding [FONT=Courier New][SIZE=2]/mnt/home-areas[/SIZE][/FONT]. It appears that might be a bug here as the first method using the bind mounts doesn't operate properly, but it is not possible to mount two different directories over the same physical device. Furthermore, I don't know why [FONT=Courier New][SIZE=2]/dev/sda4[/SIZE][/FONT] is coming up as requiring a fix when, if anything, [FONT=Courier New][SIZE=2]/dev/sda3[/SIZE][/FONT] should be the one to have something to complain about (e.g. a "double mount").

Incidentally, even though my [FONT=Courier New][SIZE=2]/etc/fstab[/SIZE][/FONT] doesn't contain the mount for [FONT=Courier New][SIZE=2]/export/home-areas[/SIZE][/FONT] any more (I have removed the mount temporarily), the errors on [FONT=Courier New][SIZE=2]/dev/sda4[/SIZE][/FONT] still persist.

Why I'm using this kind of configuration is not the issue up for discussion here. However, if anybody can see any errors in the current configuration files or the way the mounts are set up then I would welcome suggestions. Maybe then the errors on [FONT=Courier New][SIZE=2]/dev/sda4[/SIZE][/FONT] might disappear.

Thanks in advance,

---

### Post by dcstar on 2012-04-20
> **aps2012 said:**
> 
.........
Why I'm using this kind of configuration is not the issue up for discussion here. However, if anybody can see any errors in the current configuration files or the way the mounts are set up then I would welcome suggestions. Maybe then the errors on [FONT=Courier New][SIZE=2]/dev/sda4[/SIZE][/FONT] might disappear.

Thanks in advance,

For a start you should not be using /dev/sd designations for physical drives, use UUIDs as has been the recommended practice for years now.

---

### Post by aps2012 on 2012-04-20
> **dcstar said:**
> For a start you should not be using /dev/sd designations for physical drives, use UUIDs as has been the recommended practice for years now.

And so they have, except that if I had kept the UUIDs in the files then the good readers of this post wouldn't know which directory mapped to which [FONT=Courier New][SIZE=2]/dev/sda...[/SIZE][/FONT] device. The UUIDs were replaced for the sake of brevity and ease of understanding.

If you have any more suggestions then please let me know.

---

### Post by Ventiman on 2012-05-29
I have the same problem. My dmesg (bootlog) says 
.."EXT4-fs (sda7): INFO: recovery required on readonly filesystem"
.."EXT4-fs (sda7): write access will be enabled during recovery"
then it pauses for 30 seconds
.."EXT4-fs (sda7): recovery compleet"
.."EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)" 

It does this every boot. 

Could it be related to an SSD? I have and Seagate MomentusXT which is a HDD/SSD combo drive.

My fstab also has a line:
proc   /proc   proc   nodev,noexec,nosuid   0   0

What does that line do?

---

### Post by Gyokuro on 2012-05-29
Hi

I have a question concerning your post: could it be possible that you have played in the past with some mount options ? Do help more it would be really great if users can post their complete fstab not parts of the concerning file.

---

