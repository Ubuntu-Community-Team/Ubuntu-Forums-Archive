---
title: "mdadm pukes after reboot"
date: 2011-08-10
forum: General Help
---

### Post by imhotep531 on 2011-08-10
I have created a RAID 1 array using [this tutorial]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID").  Rather than reiterate everything I'll just say that I followed the instructions to the letter, including the creation of /etc/mdadm/mdadm.conf and editing /etc/fstab as instructed in the tutorial.

The problem comes when I reboot the system.  I get the following message before seeing a login prompt.

```
fsck from util-linux-ng 2.17.2
mount: wrong fs type, bad option, bad superblock on /dev/md0,
missing codepage or helper program, or other error
In some cases useful info is foundin syslog - try
dmesg tail or so

mountall: mount /home/nas [703] terminated with status 32
mountall: Filesystem could not be mounted: /home/nas
An error occurred while mounting /home/nas
Press S to skip mounting or M for manual recovery
It sounds like there are two issues, one with the array /dev/md0 itself, and one with the mount point /mnt/nas.
```

Anyone ever dealt with this before?

---

### Post by YesWeCan on 2011-08-10
Hi. Would you post your /etc/fstab and /etc/mdadm/mdadm.conf files?

---

### Post by dcstar on 2011-08-10
> **imhotep531 said:**
> I have created a RAID 1 array using [this tutorial]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID").
.........

I would recommend always using Ubuntu specific HOWTOs for this rather than generic Linux ones.

Do a web search and you will be presented with a number of options for setting up RAID on Ubuntu systems.

---

### Post by imhotep531 on 2011-08-10
> **YesWeCan said:**
> Hi. Would you post your /etc/fstab and /etc/mdadm/mdadm.conf files?

/etc/mdadm/mdadm.conf

```
ARRAY /dev/md0 UUID=3aaa0122:29827cfa:5331ad66:ca767371
```/etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b4b76f90-2a6c-4b89-a5e8-b015583f1138 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aac8d326-986a-4bbc-a68f-69c04af38b98 none            swap    sw              0       0
/dev/md0        /nas    ext4    defaults        1       2
```Also here is the bottom portion of output from fdisk -l, the bit that pertains to my RAID1 array.

```
Disk /dev/md0: 500.1 GB, 500106723328 bytes
81 heads, 63 sectors/track, 191411 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0515eb19

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      191412   488385560   fd  Linux raid autodetect
```I'm confused about this as well because I did not create /dev/md0p1.  Ubuntu seems to have created it for me and it only started showing up after the first reboot following creation of /devmd0.

---

### Post by YesWeCan on 2011-08-10
Ok. Well, mdadm works in mysterious ways.

Let's just check some basics.
Please post the output of [COLOR="Navy"]sudo blkid[/COLOR]

> It sounds like there are two issues, one with the array /dev/md0 itself, and one with the mount point /mnt/nas.

fstab tries to mount /dev/md0 at /nas not at /mnt/nas. Where is the nas directory?

The mdadm.conf file's first line should be 'DEVICES'
Like this:
```
DEVICE partitions
ARRAY /dev/md0 UUID=3aaa0122:29827cfa:5331ad66:ca767371
```

I assume you formatted the array to ext4 already?

Can you make the necessary changes to fstab and mdadm.conf?
Then run [COLOR="Navy"]cat /proc/mdstat[/COLOR]. This show you what arrays are assembled and what their status is. If you find an array listed (there may be none listed which is fine; skip the remove command)  you need to remove it and then reassemble: Suppose it is called /dev/md127. 
[COLOR="Navy"]sudo mdadm --remove /dev/md127[/COLOR]

Now reassemble
[COLOR="Navy"]sudo mdadm --assemble --scan[/COLOR]
and cat /proc/mdstat again and you should now see /dev/md0

If ok so far, then run sudo mount -a (this mounts or remounts everything specified in fstab)
Now check that your raid filesystem is mounted at nas

If ok, update the initial RAM filesystem so all these changes are recognized during boot.
[COLOR="Navy"]sudo update-initramfs -u[/COLOR]

---

### Post by imhotep531 on 2011-08-10
> **YesWeCan said:**
> Ok. Well, mdadm works in mysterious ways.

Let's just check some basics.
Please post the output of [COLOR=Navy]sudo blkid[/COLOR][/QUOTE

Here's blkid

```
/dev/sda1: UUID="b4b76f90-2a6c-4b89-a5e8-b015583f1138" TYPE="ext4"
/dev/sda5: UUID="aac8d326-986a-4bbc-a68f-69c04af38b98" TYPE="swap"
/dev/sdb1: UUID="733ef9ed-59d5-f04a-32e0-3624f2fdf684" TYPE="linux_raid_member"
/dev/sdc1: UUID="733ef9ed-59d5-f04a-32e0-3624f2fdf684" TYPE="linux_raid_member"
/dev/md0: UUID="f5b4ddd7-f2ac-4b4a-8854-53c5700c3e22" TYPE="ext4"
/dev/md0p1: UUID="6ba3298c-c52a-432b-888d-50cab92d293d" TYPE="ext4"
```> fstab tries to mount /dev/md0 at /nas not at /mnt/nas. Where is the nas directory?Thanks for catching that.  I forgot to change the mount point form a previous attempt.  Before I fix this though, I wanted to clarify something further down...

[QUOTE]The mdadm.conf file's first line should be 'DEVICES'Ok two things, first I referenced another guide and have revised mdadm.conf as follows.  Also I provided the wrong UUID in my first response.  This is the correct one and is being used in mdadm.conf now.

```
DEVICE /dev/sdb1 /dev/sdc1
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=733ef9ed:59d5f04a:32e03624:f2fdf684
```> I assume you formatted the array to ext4 already?I am confused on the point of formatting because the guide I followed said to do things in this order:

create partitions -> format partitions (I chose ext4) -> create RAID array with formatted partitions

So if I'm mirroring two partitions that are already formatted to ext4, why does Ubuntu then automatically create /dev/md0p1 on my brand new array and then I have to format it?

> Can you make the necessary changes to fstab and mdadm.conf?I sure can, I just wanted to pause here and get clarification before going further.  I want to udnerstand why /devmd0p1 suddenly appeared after rebooting and whether or not I really need to format the array when it is comprised of two already formatted partitions.

Thanks again for your help!

---

### Post by YesWeCan on 2011-08-10
> **imhotep531 said:**
> Ok two things, first I referenced another guide and have revised mdadm.conf as follows.  Also I provided the wrong UUID in my first response.  This is the correct one and is being used in mdadm.conf now.
It is better to use 'DEVICE partitions' rather than specifying the partition numbers because it is more tolerant to changes in disk order. It is sort of over-specifying because it is the UUID that matters.

> I am confused on the point of formatting because the guide I followed said to do things in this order:

create partitions -> format partitions (I chose ext4) -> create RAID array with formatted partitions

So if I'm mirroring two partitions that are already formatted to ext4, why does Ubuntu then automatically create /dev/md0p1 on my brand new array and then I have to format it?
When you create an md array it is like creating a new partition. It needs to be formatted. Even tho it was created from pre-formatted partitions. In fact, the original partitions didn't need to be preformatted at all.
So go ahead and format the md0 once you have it assembled and appearing ok in /proc/mdstat.
[COLOR="Navy"]sudo mkfs.ext4 /dev/md0[/COLOR]
I'm not sure yet where this md0p1 is coming from. Let's try out your changes and reboot and see what is what.

> I sure can, I just wanted to pause here and get clarification before going further.  I want to udnerstand why /devmd0p1 suddenly appeared after rebooting and whether or not I really need to format the array when it is comprised of two already formatted partitions.
Sure.

BTW which version of Ubuntu are you using?

---

### Post by imhotep531 on 2011-08-10
Ok, thanks for the clarification.  I was mistaken.  The guide I was following never said to format the partitions before creating the array.

So I formatted /dev/md0 to ext4.  Done and successful.  Now fdisk -l shows the following:

```
Disk /dev/md0: 500.1 GB, 500106723328 bytes
2 heads, 4 sectors/track, 122096368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```I consistently get this message about lacking a valid partition table, but I read in another thread this error can be ignored.  So I'll do that and press on.

/etc/mdadm/mdadm.conf now says the following:

```
DEVICES
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=d26d244d:c37fae26:ed25f1fb:7ad82b8c
```/etc/fstab now says the following:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b4b76f90-2a6c-4b89-a5e8-b015583f1138 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aac8d326-986a-4bbc-a68f-69c04af38b98 none            swap    sw              0       0
/dev/md0        /mnt/nas        ext4    defaults        0       0
```Mounted, now checking with df -k

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73744616   1279140  68719428   2% /
none                   1958756       236   1958520   1% /dev
none                   1963192         0   1963192   0% /dev/shm
none                   1963192       292   1962900   1% /var/run
none                   1963192         0   1963192   0% /var/lock
none                   1963192         0   1963192   0% /lib/init/rw
none                  73744616   1279140  68719428   2% /var/lib/ureadahead/debugfs
/dev/md0             480720528    202664 456098592   1% /mnt/nas


```cat /proc/mdstat

```
Personalities : [raid1]
md0 : active raid1 sdc1[1] sdb1[0]
      488385472 blocks [2/2] [UU]

unused devices: <none>
```
Everything looks good.  Rebooting....

---

### Post by imhotep531 on 2011-08-10
Forgot to mention, I also did the update-initramfs -u command before rebooting.

I'm getting the same error I listed in my original post.

---

### Post by YesWeCan on 2011-08-10
Sorry I must be half asleep today. The mdadm.conf directive should be:
DEVICE partitions

Fix this and then run sudo update-initramfs -u again and then reboot.

---

### Post by Habitual on 2011-08-10
YesWeCan:
can't ```
ARRAY /dev/md0 level=raid0 devices=/dev/sdc1,/dev/sdb1
``` be used in /etc/mdadm/mdadm.conf?

Does it HAVE to be UUID format?

I am just curious. Thanks.

Subscribed with interest.

---

### Post by YesWeCan on 2011-08-10
> **Habitual said:**
> YesWeCan:
can't ```
ARRAY /dev/md0 level=raid0 devices=/dev/sdc1,/dev/sdb1
``` be used in /etc/mdadm/mdadm.conf?

Does it HAVE to be UUID format?

I am just curious. Thanks.

Subscribed with interest.
Yes, as long as the devices listed are members of those specified by the DEVICE statement.
See man mdadm.conf
UUIDs with a "scan all devices" DEVICE statement is usually more reliable because the disk names can change sometimes, either the bios renames them or you add or remove a disk, and then your arry wont assemble.

---

### Post by Habitual on 2011-08-10
thanks.:D

---

### Post by imhotep531 on 2011-08-11
Well, I've edited mdadm.conf to say "DEVICE Partitions", but that pesky /dev/md0p1 showed up again after the reboot.  I can't get it to go away.  It shows up when I run fdisk -l, but when I use fdisk to delete that partition it says "no partition defined yet!"

This has been par for the course for me so far.  Ubuntu contradicts itself a lot.  Going three weeks now trying to setup a simple RAID 1.

When I run partprobe it now says

```
Error: Can't have a partition outside the disk!
```

No kidding Ubuntu.  You tell me how there's a partition outside a disk?

Anyway I uninstalled and reinstalled mdadm and afterward fdisk would let me delete the /dev/md0p1 partition that I never created and doesn't really exist but actually does exist even though you can't have one outside a disk...

Here is the best part -- after removing mdadm I'm showing an active array called /dev/md0 when I run cat /proc/mdstat.  Huh?!?!?

Next I reinstalled mdadm and was able to stop the /dev/md0 array before creating it anew.  Right now the array is syncing up, I'll report back in a few hours when that's done and I can reboot again.

---

### Post by imhotep531 on 2011-08-11
Ok, I have a new problem.  After recreating /dev/md0 and confirming the array is active using cat /proc/mdstat, I checked with fdisk -l and it's not showing either of the partitions that are part of /dev/md0.

How on earth can /dev/md0 be active if /dev/sdb1 and /dev/sdc1 aren't there?

It gets better...

```
root@datahaus:/home/imhotep531# partprobe
Warning: WARNING: partition(s) 1 on /dev/sdb could not be modified, probably because it/they is/are in use.  As a result, the old partition(s) will remain in use until after reboot. You should reboot now before making further changes.
Warning: WARNING: partition(s) 1 on /dev/sdc could not be modified, probably because it/they is/are in use.  As a result, the old partition(s) will remain in use until after reboot. You should reboot now before making further changes.

```

---

### Post by YesWeCan on 2011-08-11
Perhaps it's time for a short-cut.
You can create the RAID using Disk Utility.
But first you should delete what you have got.

Stop the raid
sudo madam -S /dev/md0

Erase the superblocks
sudo mdadm --zero-superblock /dev/sd[bc]1

Edit mdadm.conf and delete the ARRAY statement

Run /System/Apps/Disk Utility
Delete partitions sdb1 and sdc1, leaving just empty space.
File/Create/RAID Array...
Choose RAID1
Give it a name that has no spaces in it
Select the empty spaces on sdb and sdc to use for the array
Once created, format it to ext4
Close Disk Utility

cat /proc/mdstat
it should be called /dev/md0

sudo mdadm -Ds
copy the ARRAY line to the mdadam.conf file

sudo mount -a
check it has mounted the new array at /mnt/nas

sudo update-initramfs -u

Reboot.

---

### Post by YesWeCan on 2011-08-11
> **imhotep531 said:**
> Well, I've edited mdadm.conf to say "DEVICE Partitions", but that pesky /dev/md0p1 showed up again after the reboot.  I can't get it to go away.
It turns out that this is a feature of md raid. It is possible to make a raid partition that can be partitioned, so md0p1 stands for array md0 partition 1.
According to 'man mdadm' this requires creating the array and using the --auto=mdp (or part or p). It defaults to making a non-partitionable raid if this is not specified.

---

### Post by imhotep531 on 2011-08-11
I really appreciate your efforts to help me.  At this point I'm going to throw in the towel.  IMHO something as basic as RAID1 should not be this difficult to set up.  It took minutes to get it going on my old Windows XP machine and it never had a single problem.  I was persuaded to try Linux because my two goals (home webserver and nas) could be met with an open source operating system, and I could get a second life out of an old PC.  But so far I keep hitting walls and their not even consistent.  I'm not bashing just trying to be practical.  I really admire you guys who have a talent for figuring this stuff out and I appreciate your time trying to help me.  I need to move on to something more familiar so I can be productive again.

---

### Post by YesWeCan on 2011-08-11
Linux is a bit like this sometimes. If you already know how something works you can see how easy it is to do something. That's  not much consolation, tho.

If you do try this again I suggest using Disk Utility as I described; it makes it much easier. Try to use Ubuntu Official guides or Ubuntu Community guides. :)

---

