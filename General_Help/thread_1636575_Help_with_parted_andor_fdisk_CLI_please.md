---
title: "Help with parted and/or fdisk CLI please"
date: 2010-12-03
forum: General Help
---

### Post by kansasnoob on 2010-12-03
I've searched the world over off and on for a long time and never have found an answer to this, but I believe everything that can be seen in a GUI can also be seen using the CLI :)

What I'm wondering is how to get either parted or fdisk to also display "used" and "unused" like Gparted does. Example:

[ATTACH]177278[/ATTACH]

```
lance@lance-desktop:~$ sudo parted /dev/sdb print
[sudo] password for lance: 
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  76.7GB  76.7GB  primary   ext4
 2      76.7GB  80.0GB  3305MB  extended
 5      76.7GB  80.0GB  3305MB  logical   linux-swap(v1)

```

```
lance@lance-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004015a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9328    74920960   83  Linux
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

```

```
lance@lance-desktop:~$ sudo fdisk -lu

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004015a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   149843967    74920960   83  Linux
/dev/sdb2       149846014   156301311     3227649    5  Extended
/dev/sdb5       149846016   156301311     3227648   82  Linux swap / Solaris

```

I tend to prefer the descriptive nature of parted, but I wonder if it's even possible to show the "used" and "unused" in the terminal.

It's not a big deal but it could be useful when trying to troubleshoot problems without requiring a screenshot, or with multiple drives - multiple screenshots :)

No rush, just something I've long wondered about.

---

### Post by skymera on 2010-12-03
This isn't fdisk but try

```
 df -h 
```

Does that help at all? I'm in Windows atm (grr) so can't double check, but it's safe to run!

---

### Post by The Cog on 2010-12-03
I think that gparted mounts the partitions in order to be able to df them. I have noticed that it doesn't report the usage of partition types that can't easily be mounted (e.g. jfs partitions if jfstools isn't installed).

So I think the command-line way to do this would be to create mount points, mount the partitions in question and use df and maybe then unmount them again. Long-winded but do-able. A script would help.

---

### Post by dcstar on 2010-12-04
> **kansasnoob said:**
> I've searched the world over off and on for a long time and never have found an answer to this, but I believe everything that can be seen in a GUI can also be seen using the CLI :)

What I'm wondering is how to get either parted or fdisk to also display "used" and "unused" like Gparted does.
........

```
#!/bin/sh -

# dfspace - d(isk) f(ree) space
#
# Calculate available disk space in all mounted filesystems
# with the exception of psuedo file systems such as /proc and /dev/fd.
#
# Alternately, report on filesystems/devices specified on cmd-line.
#   Filesystem may be 1K bytes/block, but, df uses 512 bytes/block.
#

# get free and allocated space.
df -k $* 2>/dev/null | awk '
BEGIN {  AVAIL=0; TOTAL=0 }
{
	if ( $6 != "/proc" && $6 != "/dev/fd" && $1 != "Filesystem" )
	{
#print $1 $2 $3 $4 $5 $6
		AVAIL += $4
		TOTAL += $2
		while (length($6)<28) $6 = $6 " "
		printf("%s: %#7.2f MB of %#7.2f MB available (%#6.2f%%)\n",$6, $4 / 1024, $2 / 1024, $4 * 100 / $2 )

	}
}
END { printf("-------------------------------------------------------------------------------\n")
printf("%s: %#7.2f MB of %#7.2f MB available (%#6.2f%%)\n",
	"            Total           ", AVAIL / 1024, TOTAL / 1024, AVAIL * 100 / TOTAL)

}'

# end of disk space calculation.
```

---

### Post by asmoore82 on 2010-12-04
You don't *have* to mount filesystems to retrieve this information,
but that is probably the easiest way.

gparted probably "pokes" at the filesystems with filesystem specific tools to calculate this info.
One possible method for ext filesystems would be:
```
sudo dumpe2fs -h /dev/sda1 | grep -i block
```

`fdisk` would be completely incapable in this area. One of the major differences between the `fdisk` families and `parted` families is that `fdisk` only handles partitioning, it doesn't touch the filesystems within the partitions. This isn't an `fdisk` bug, it is by design.

---

### Post by asmoore82 on 2010-12-04
> **dcstar said:**
> ```
#!/bin/sh -
...

```

How is this better/worse than a simple ```
df -h -x proc -x tmpfs -x devtmpfs
```

----------------
By the way,
This line is wrong: ```
df -k $* 2>/dev/null | awk '
```
It should be: ```
df -k **[COLOR="Purple"]"$@"[/COLOR]** 2>/dev/null | awk '
```

---

### Post by kansasnoob on 2010-12-07
Sorry to take so long responding, I've been buried in other work.

When I use "df" I usually use a capital H, not much difference:

```
lance@lance-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda17             20G  3.9G   15G  21% /
none                  995M  304K  995M   1% /dev
none                 1002M  212K 1001M   1% /dev/shm
none                 1002M   92K 1001M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda17              22G   4.2G    16G  21% /
none                   1.1G   312k   1.1G   1% /dev
none                   1.1G   218k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock

```

Anyway I'm not even sure how to run dcstar's script :confused:

I don't even use an actual script to perform a chroot, I just do this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

It might help to know what I'm up to :)

I recently posted this:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

And I hope to provide a few common partitioning scheme examples in the near future. I was going to conclude the "examples" post with something like:

"If you have the slightest doubt about how to proceed please start a new thread at Installation & Upgrades and include the following info" ... blah. blah.

Anyway I'm thinking 90% of people asking for help will be Windows users so it's probably best to just start with "sudo fdisk -l" and work from there requesting additional info, including a screenshot of Gparted if needed.

Sometimes the output of the Boot Info Script can be very helpful determining exactly what NTFS partitions serve what purpose.

It's becoming quite common for branded Win7 computers to have 4 primary partitions and, combined with some recent changes to ubiquity, I've seen somewhat of an uptick in the number of new users reporting data/OS loss :eek:

I was just in hopes that there were a way to get parted to provide a verbose output that would provide all of the info Gparted provides. Can't blame me for asking ;)

---

