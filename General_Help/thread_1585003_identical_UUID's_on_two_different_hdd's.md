---
title: "identical UUID's on two different hdd's"
date: 2010-09-29
forum: General Help
---

### Post by revtds on 2010-09-29
I have three posts at [http://ubuntuforums.org/showthread.php?t=1574062&highlight=ecryptfs]("http://ubuntuforums.org/showthread.php?t=1574062&highlight=ecryptfs") which detail an issue with ecryptfs and a new Lucid install.

I have discovered that I have two partitions, on separate hdd's with identical UUID's, and the system switches back and forth erratically on restarts between the two different partitions, giving me the current /home or the /home of two months ago when I did the upgrade.

Any insight into this and how to correct it would be a great help.

Thank you,

---

### Post by drs305 on 2010-09-29
I don't use or have much knowledge about ecryptfs, so if anything I say goes against what you know about ecryptfs, go with what you know.

You can change the UUID simply with the command:

```
sudo tune2fs -U random /dev/sdXY  # Example /dev/sda1
```

If you change one of the partition UUIDs, edit and change the partition's UUID in /etc/fstab and run "sudo update-grub" to make sure the new UUID is incorporated into the Grub2 menu.

```

sudo blkid -c /dev/null  # View UUIDS
sudo update-grub
gksudo gedit /etc/fstab /boot/grub/grub.cfg  # Open fstab and grub.cfg for review and editing.

```

You should check to make sure at least these two files are correct. Check the "blkid" command results and the entries in the grub.cfg and fstab files to make sure the UUIDs match.

For fstab, if it isn't your Ubuntu partition, close all your apps and run the following two commands. The first will attempt to unmount non-system partitions (you will get some busy messages). The second will attempt to mount all the partitions listed in fstab. The goal of the second command is to have it run without generating *any* messages, which means the entries all mounted properly.
```
sudo umount -a
sudo mount -a
```

---

### Post by Seq on 2010-09-29
> **revtds said:**
> I have three posts at [http://ubuntuforums.org/showthread.php?t=1574062&highlight=ecryptfs]("http://ubuntuforums.org/showthread.php?t=1574062&highlight=ecryptfs") which detail an issue with ecryptfs and a new Lucid install.

I have discovered that I have two partitions, on separate hdd's with identical UUID's, and the system switches back and forth erratically on restarts between the two different partitions, giving me the current /home or the /home of two months ago when I did the upgrade.

Any insight into this and how to correct it would be a great help.

Thank you,

I just read your other thread. You're right in that it is not normally possible that two filesystems have the same UUID. But you told gparted to copy the filesystem, so there you go. Copies are identical. Also note that UUIDs are assigned to the filesystem, not the partition, an important distinction.

Since you want to keep the filesystem on sda7 going forward, you will want to assign a new UUID to the one on sdb2. You can do this with tune2fs.

```
sudo tune2fs -U random /dev/sdb2
```

---

### Post by srs5694 on 2010-09-30
> **Seq said:**
> Also note that UUIDs are assigned to the filesystem, not the partition, an important distinction.

One minor point: This is true on Master Boot Record (MBR) disks. The GUID Partition Table (GPT), however, assigns a GUID (a minor variant of a UUID) to partitions. The UUID in the filesystem remains, of course, and AFAIK the GUID assigned to the partition in the GPT isn't used by Linux for anything, aside from being accessible by some partitioning tools. I mention this because there's potential for confusion if somebody is using GPT, since there could be a GUID and a different UUID associated with a single partition/filesystem. GPT also uses a GUID for a partition type code. For instance:

```

# sgdisk -i 1 /dev/sda
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: EA7D2AA8-6FC1-4182-B4A5-B047FDEE34C4
First sector: 34 (at 17.0 KiB)
Last sector: 390625 (at 190.7 MiB)
Partition size: 390592 sectors (190.7 MiB)
Attribute flags: 0000000000000000
Partition name: Unused

# blkid /dev/sda1
/dev/sda1: LABEL="spare1" UUID="f12ca6d0-40f1-416c-86fd-b65c934cc750" TYPE="ext2"

```

GPT users must be careful to keep these values straight; substituting a partition GUID for the UUID value in /etc/fstab, for instance, will not work. (I know; I've tried, just to see what would happen.)

---

### Post by revtds on 2010-10-01
Thanks to all of you for your help.  Currently, I have one line in fstab commented out, and a new line inserted, directing the system to boot with the most current partition, sdb2.

I was able with your help to change the UUID and get control of my system, but now when I boot into GParted Live, and try to copy the current partition form sdb2 to sda7 in order to only have the most current data available, and then change sda into a backup disk, GParted does not seem to want to let me copy the partition.  I did it before, which got me into the mess, but now it won't. When I mount the partitions into media with separate mountpoints, it shows a lock on the partition and won't let me copy.  

I will keep digging on that, but again, thank you. I understand what and how it happened, to avoid that in the future.  I am using grub, so no need to worry about the other boot system, although that is good info to know.

I will mark this solved and work on the partition copy issue some more.

---

### Post by SeijiSensei on 2010-10-01
Are you just trying to make a bit-for-bit copy of one partition to another identically sized partition?  You can do this with "dd if=/dev/sda1 of=/dev/sdb1".  Both partitions will naturally need to be unmounted to do this.  Boot from a rescue CD, then run the command in a terminal.

---

### Post by drs305 on 2010-10-01
> **revtds said:**
>  When I mount the partitions into media with separate mountpoints, it shows a lock on the partition and won't let me copy.  

Are you doing this with the Gparted LiveCD? With this or the Ubuntu LiveCD, the partitions should start off unmounted and should remain so if you intend to copy them. You shouldn't (need to) mount them to perform the copy operation.  For the LiveCD, you have to unmount the swap partition (Highlight the swap partition, then: Partition, swapoff) as well before creating a new partition.

---

### Post by dcstar on 2010-10-02
You can also change the UUID of a NTFS partition with a one-line script I created a few weeks ago, do a forum search for the thread if you need it.

---

