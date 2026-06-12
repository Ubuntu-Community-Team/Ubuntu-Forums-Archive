---
title: "Unable to Mount Partitions"
date: 2012-06-12
forum: General Help
---

### Post by ultrageeky on 2012-06-12
Since yesterday's update, I've been unable to mount partitions.

My HDD is split into multiple partitions (2 primary and several extended). The only partitions that mount are /root and /swap. Nothing happens when I try to mount other partitions by clicking them in Dolphin. Nothing happens when I try to mount other partitions with **sudo mount -a**.

I can mount them individually with:

sudo /usr/bin/udisks --mount /dev/sdc4

But attempts to access partitions mounted like this lead to a non existent drive error.

Partition Manager shows the drives and partitions but does not provide an option to mount them.

This is the case with all internal drives attached to my computer (3 drives in total). It is the same for USB flash drives when connected to my computer. It is the same for CD/DVD drives attached to my computer.

So, the drives are detected by the OS but I'm unable to mount and access them. Other devices attached to the computer work fine. The keyboard I'm using to type this is USB so the ports work fine.

I noticed the fault after yesterday's updates. How can I fix this so that my drives automount again?

---

### Post by ultrageeky on 2012-06-12
Solved it, kind of.

Had to recreate fstab using the output of **sudo blkid** and a little rearrangement of the output.

Downside to this: all partitions listed in fstab mount when the OS loads. My DVD drive doesn't mount and flash drives do not mount; though they would if I added them to fstab.

Any proper solutions warmly appreciated.

---

### Post by ultrageeky on 2012-06-13
Still looking for a better solution, if anyone has one.

---

### Post by wilee-nilee on 2012-06-13
It would help to know the partition file types and what they are for.

You might start with a screenshot of the partitioner, in ubuntu it is gparted, not sure in kubuntu.

If any of them are ntfs partitions they may need a chkdsk possibly.

You would run a chkdsk from windows.

The devil is in the details always. ;)

---

### Post by ultrageeky on 2012-06-14
Thanks for your reply, wilee-nilee.

All partitions are Linux ext4, ext3 and swap partitions. Windows is only installed via VirtualBox on a virtual disc.

The issue I'm having is that where Kubuntu once auto mounted drives and removable drives, it now only mounts them when I manually mount them and create mount points for them or when they are set in fstab.

As you ask:

The output from

**fdisk -l**

Blank. Nothing shown at all.

The output from

**mount**

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /Backups type ext4 (rw)
/dev/sda6 on /VirtualOS type ext4 (rw)
/dev/sda7 on /Videos type ext4 (rw)
/dev/sda8 on /Music type ext4 (rw)
/dev/sda9 on /Audio_Books type ext4 (rw)
/dev/sda10 on /Text_Books type ext4 (rw)
/dev/sda11 on /Software type ext4 (rw)
/dev/sda12 on /Photos type ext4 (rw)
/dev/sda13 on /Documents type ext4 (rw)
/dev/sdb1 on /Virtual_OS type ext3 (rw)
/dev/sdb2 on /VOS_Software type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)

```The output from

**sudo blkid**

```
/dev/sda1: UUID="b7cc1889-eca3-46cc-a72b-5bff57fb523a" TYPE="ext4" 
/dev/sda3: LABEL="Backups" UUID="51a38068-660a-4fbc-b2a1-9d93835591ae" TYPE="ext4" 
/dev/sda5: UUID="70e6fc7c-192b-4660-9041-fa2152ac66a2" TYPE="swap" 
/dev/sda6: LABEL="VirtualOS" UUID="c6a4ae27-4790-4b8e-bc98-b8873bc89cbc" TYPE="ext4" 
/dev/sda7: LABEL="Videos" UUID="2f5f850f-8ea5-4c31-b5ff-aca493d8c303" TYPE="ext4" 
/dev/sda8: LABEL="Music" UUID="47a076cf-72c6-4827-9f96-a3657d0eae03" TYPE="ext4" 
/dev/sda9: LABEL="Audio Books" UUID="a880047c-94bb-42b5-8449-9a7e091055ed" TYPE="ext4" 
/dev/sda10: LABEL="Text Books" UUID="8440c846-0723-4a8c-a19c-6ca683d904b7" TYPE="ext4" 
/dev/sda11: LABEL="Software" UUID="12e1553f-2344-4849-a410-3294c7517515" TYPE="ext4" 
/dev/sda12: LABEL="Photos" UUID="912d55a5-ec92-49b5-b758-8a90899c6384" TYPE="ext4" 
/dev/sda13: LABEL="Documents" UUID="0afadb66-5a18-4d18-9a4e-f73a1d148563" TYPE="ext4" 
/dev/sdb1: LABEL="Virtual OS" UUID="2270162a-7f4a-40fd-a792-011a3f1d3124" TYPE="ext3" 
/dev/sdb2: LABEL="VOS Software" UUID="9ae168d7-1384-459a-8e19-488f656938a2" TYPE="ext3" 
/dev/zram0: UUID="2f68b584-be50-44ff-9eed-3aa58211660e" TYPE="swap" 

```The output from

**cat /etc/mtab**

```

/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /Backups ext4 rw 0 0
/dev/sda6 /VirtualOS ext4 rw 0 0
/dev/sda7 /Videos ext4 rw 0 0
/dev/sda8 /Music ext4 rw 0 0
/dev/sda9 /Audio_Books ext4 rw 0 0
/dev/sda10 /Text_Books ext4 rw 0 0
/dev/sda11 /Software ext4 rw 0 0
/dev/sda12 /Photos ext4 rw 0 0
/dev/sda13 /Documents ext4 rw 0 0
/dev/sdb1 /Virtual_OS ext3 rw 0 0
/dev/sdb2 /VOS_Software ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0

```The fstab file I created is:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b7cc1889-eca3-46cc-a72b-5bff57fb523a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=70e6fc7c-192b-4660-9041-fa2152ac66a2 none            swap    sw              0       0
# /dev/sda3:
UUID=51a38068-660a-4fbc-b2a1-9d93835591ae  /Backups ext4  defaults 0 0
# /dev/sda6:
UUID=c6a4ae27-4790-4b8e-bc98-b8873bc89cbc  /VirtualOS ext4  defaults 0 0
# /dev/sda7:
UUID=2f5f850f-8ea5-4c31-b5ff-aca493d8c303  /Videos ext4  defaults 0 0
# /dev/sda8:
UUID=47a076cf-72c6-4827-9f96-a3657d0eae03  /Music ext4  defaults 0 0
# /dev/sda9:
UUID=a880047c-94bb-42b5-8449-9a7e091055ed  /Audio_Books ext4  defaults 0 0
# /dev/sda10:
UUID=8440c846-0723-4a8c-a19c-6ca683d904b7  /Text_Books ext4  defaults 0 0
# /dev/sda11:
UUID=12e1553f-2344-4849-a410-3294c7517515  /Software ext4  defaults 0 0
# /dev/sda12:
UUID=912d55a5-ec92-49b5-b758-8a90899c6384  /Photos ext4  defaults 0 0
# /dev/sda13:
UUID=0afadb66-5a18-4d18-9a4e-f73a1d148563  /Documents ext4  defaults 0 0
# /dev/sdb1:
UUID=2270162a-7f4a-40fd-a792-011a3f1d3124  /Virtual_OS ext3 defaults 0 0
# /dev/sdb2:
UUID=9ae168d7-1384-459a-8e19-488f656938a2  /VOS_Software  ext3 defaults 0 0

```I think a few items of software must have been removed during an update. Any idea what those software might be?

---

### Post by wilee-nilee on 2012-06-14
So with a fdisk -l showing nothing and the rest showing, this is a bit beyond my pay range. ;)

I'm not sure how significant this is but the last swap in the blkid is not in the fstab, zram0 I am not familiar with what that is. Your blkid does show in the fstab as correct, but I did not look for any extra fstab stanzas or if any are incorrect beyond the UUID.
```
/dev/zram0: UUID="2f68b584-be50-44ff-9eed-3aa58211660e" TYPE="swap"
```I suspect that there may be a broken partition table in the sda, this is just a theory though, but the sdb does not show as well in the fdisk.

Lets see what others have to say, would be how I roll here.

It might help to have the bootscript posted as just more info.

Use this tool and the bootinfo summary to get a HTTP address to post.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This version of the script has some extra debugging stuff that the regular script does not have.

---

### Post by kanikilu on 2012-06-14
**fdisk -l** should show something with **sudo**. I want to say that it used to warn you that it should be run as root/with sudo, but that doesn't seem to be the case anymore.

Anyways, with devices not automatically mounting, to me it seems like there may be a problem with udev. I'm not entirely sure how to troubleshoot it from here, but in this thread, simply reinstalling udev fixed problems for a couple people...

[http://ubuntuforums.org/showthread.php?t=1767077](http://ubuntuforums.org/showthread.php?t=1767077)

---

### Post by ultrageeky on 2012-06-14
Thank you both. Absolutely right about fdisk needing to be run in sudo. I could slap myself sometimes. I'm  going to reinstall udev but I now know what fdisk knows ;)

**fdisk -l**

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005412f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97656831    48827392   83  Linux
/dev/sda2        97658878  1835937791   869139457    5  Extended
/dev/sda3      1835940330  1953520064    58789867+  83  Linux
/dev/sda5        97658880   117188607     9764864   82  Linux swap / Solaris
/dev/sda6       117190656   312500223    97654784   83  Linux
/dev/sda7       312502272   926902271   307200000   83  Linux
/dev/sda8       926904320  1317535743   195315712   83  Linux
/dev/sda9      1317538908  1419937154    51199123+  83  Linux
/dev/sda10     1419939840  1522337791    51198976   83  Linux
/dev/sda11     1522339840  1679689727    78674944   83  Linux
/dev/sda12     1679691776  1741131775    30720000   83  Linux
/dev/sda13     1741133824  1835937791    47401984   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00083b24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   204802047   102400000   83  Linux
/dev/sdb2       204802048   390721535    92959744   83  Linux
```

I would have suspected a partition table error but I can access all partitions on the drives and  flash drives do not auto mount either. USB devices work so.......

Checking out Boot Repair too. Will post back with my results.

---

### Post by ultrageeky on 2012-06-14
The results from Boot Repair are at [Ubuntu Pastebin]("http://paste.ubuntu.com/1041432/")

Re-installing udev and half a dozen other things plus doing an **apt-get build-dep** before re-installation failed to solve the issue.

I am now able to mount USB sticks automatically since installing **usbmount**. I'm still not able to  automount hdd and DVD devices.

---

### Post by ultrageeky on 2012-06-15
I don't like to think that re-installation is the only option but is it?

---

### Post by oldfred on 2012-06-19
So did problem resolve itself?

I do not know the details of Kubuntu, but am familar with Ubuntu and mount several partitions without issue.

---

