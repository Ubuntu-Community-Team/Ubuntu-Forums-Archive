---
title: "tune2fs not working for 2TB HDD, please help!!!"
date: 2010-10-18
forum: General Help
---

### Post by RM777 on 2010-10-18
I have a Western Digital 2TB HDD on Ubuntu 9.10. This is my secondary HDD which is used only for Storage of media files. I mount it as & when needed only to stream my media content.

I have tried many times to use tune2fs to free up the extra space which has been reserved automatically by linux yet although it accepts the commands & doesnt give back any errors, when I run the df- h or du- h commands, linux has still reserved 200GB & I only have 1.8TB to use. This extremely annoying as Im quickly filling it up with about 400GB currently available for me, that could easily be 500GB.

My primary drive is a seperate HDD of 320GB
Storage is /dev/sdb1 for which I mount it to a folder called 'media-centre'.

Then after mounting, I run the command: tune2fs -m 0 /dev/sdb1 media-centre

I takes the command with no problems, I run df -h, & no joy.

I have read my books at home as well as google searches & forums. Am I missing something simple here, does this command work only with certain types of HDD's?

I posted on another forum & followed a post that said I should convert from ext3 to ext2 as the journal is the cause, I ran
a tune2fs -O ^has_journal etx2 /dev/sdb1 (something like that) & checked /etc/fstab which did not reference my storage HDD. 

I greatly appreciate anyones time in reading, commenting & helping me find a solution.

Thanks

---

### Post by srs5694 on 2010-10-18
I suspect that this is a question of terabytes (TB) vs. tebibytes (TiB). See [this site](http://physics.nist.gov/cuu/Units/binary.html) for details. Disk manufacturers invariably use power-of-ten units, such as terabytes; but most disk utilities work in power-of-2 units, such as tebibytes. At the terabyte/tebibyte level, 2 TB = 1.82 TiB.

If you need more help, please post the output of the following commands, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility:

```

fdisk -lu /dev/sdb
df -h
sudo dumpe2fs -h /dev/sdb1

```

Also, I do *not* recommend disabling the journal on a disk as large as you've got. Doing so will ensure phenomenally long startup or partition mount times whenever the system crashes, suffers a power loss, or otherwise requires checking. You should re-enable that journal ASAP. In fact, for large media files, ext4fs or XFS would be a better choice than ext3fs. It's possible to convert ext3fs to ext4fs without too much pain, but converting to XFS would require backing up, creating a new filesystem, and then restoring your data.

---

### Post by RM777 on 2010-10-19
Thanks for the prompt reply, as requested here is the output;


```
root@Black:/home/rasheed# fdisk -lu /dev/sdb1

Disk /dev/sdb1: 2000.4 GB, 2000396289024 bytes
255 heads, 63 sectors/track, 243200 cylinders, total 3907024002 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb1 doesn't contain a valid partition table


root@Black:/home/rasheed# df -h /dev/sdb1
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             1.8T  1.4T  472G  75% /home/rasheed/media-centre



root@Black:/home/rasheed# dumpe2fs -h /dev/sdb1
dumpe2fs 1.41.11 (14-Mar-2010)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          4f08947a-dbc2-4a4d-a7d0-3456dd85f4ed
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              122101760
Block count:              488378000
Reserved block count:     0
Free blocks:              123716569
Free inodes:              122093835
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      907
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Sat Jun 12 13:44:45 2010
Last mount time:          Tue Oct 19 10:50:15 2010
Last write time:          Tue Oct 19 10:50:15 2010
Mount count:              133
Maximum mount count:      -1
Last checked:             Sat Jun 12 13:44:45 2010
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      c2132b24-fe92-4c05-8849-3785da36d010
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x00005cc2
Journal start:            0
```


Please note, this is a storage only HDD with no OS. I only mount it when linux has booted on the main hdd which is a seperate physical 320GB HDD.

Regards

---

### Post by RM777 on 2010-10-19
I just wanted to add, I never have to wait long at all for the drive to mount. Literally mounts as soon as the command is entered. It will only take a bit of time due to ungraceful logoff such as powering down without unmounting. Then I may have to wait a minute or so. So I dont think on this HDD that journalling will be an issue.

---

### Post by srs5694 on 2010-10-19
Please, when you're asked to use [noparse]```
[/noparse]/[noparse]
```[/noparse] blocks, do so; that preserves the original formatting, which makes tabular output (such as "fdisk -lu" and "df -h" output) legible. See [here](http://www.vbulletin.com/forum/misc.php?do=bbcode) for details and examples (search for "[noparse][code][/noparse]").

You're not missing any space. As I suspected, this is a terabyte/tebibyte confusion issue. Your disk is 2,000,396,289,024 bytes (2 TB or 1.82 TiB) in size, and that's what df is reporting. (The -h option to df reports in power-of-2 units.) Your dumpe2fs output shows no reserved blocks. It looks like you've re-enabled your journal (or the command you used to disable it didn't work), which is good.

---

### Post by RM777 on 2010-10-20
Dude

many thanks for your time in reading this. Soz about the code thing, I rushed through the email but I know what you meant & it makes sense.

I guess all I can do is wait for the Western Digital 3TB drive to come out & get that. Either that or a 3 bay shuttle PC with 3 x 2/3TB HDDs!!!

Why the industry use this Tebibyte thing is beyond me & quite confusing, anyway at least I know Im using the whole drive.

Regards

---

### Post by coffeecat on 2010-10-20
> **RM777 said:**
> Why the industry use this Tebibyte thing is beyond me & quite confusing

What is confusing is people using the term terabyte when they mean tebibyte. Tera - giga - mega - kilo - are multiples of 1000 and are the prefixes used by the International System of Units (SI). Tebi - gibi - mibi - kibi are multiples of 1024 which make sense in the computer field. The fact that some geeks have used the SI prefixes for multiples of 1024 has little or no justification beyond tradition. But since the International System of Units grew out of the metric system which itself dates back to 18th century France, I think it's fair to say that the International System can claim prior art. :wink:

---

### Post by psusi on 2010-10-20
> **RM777 said:**
> 
Then after mounting, I run the command: tune2fs -m 0 /dev/sdb1 media-centre

You use tune2fs on an UNMOUNTED partition.  The effects take place the next time you mount it.

---

### Post by CharlesA on 2010-10-20
> **RM777 said:**
> 
Why the industry use this Tebibyte thing is beyond me & quite confusing, anyway at least I know Im using the whole drive.

It's just the way drive manufactures measure space. They use 1000 instead of 1024. There is a notice on any drive where it says: 1 GB = 1,000,000,000 bytes.

> **coffeecat said:**
> What is confusing is people using the term terabyte when they mean tebibyte. Tera - giga - mega - kilo - are multiples of 1000 and are the prefixes used by the International System of Units (SI). Tebi - gibi - mibi - kibi are multiples of 1024 which make sense in the computer field. The fact that some geeks have used the SI prefixes for multiples of 1024 has little or no justification beyond tradition. But since the International System of Units grew out of the metric system which itself dates back to 18th century France, I think it's fair to say that the International System can claim prior art. :wink:

+1. :)

---

### Post by psusi on 2010-10-20
It isn't a question of SI being first, last, right, or wrong.  Everybody else in the computer industry used 1024.  A 1.44 MB floppy was exactly 1440 * 1024 bytes.  A 1 GB ram module is 1024 * 1024 * 1024 bytes.  It is only hard disk manufacturers that refused to conform to the standards and practices of the industry, because their marketing people wanted to make their drives sound larger than they are.

---

### Post by srs5694 on 2010-10-20
It's not quite that simple, psusi. Although power-of-2 units have historically been more common in computers, there are other cases where power-of-10 units have been used. Data transfer rates have usually been reported in this way, for instance. Yes, the disk manufacturers were the oddballs compared to most disk utilities in the past, but it's now obvious that their view of things, long at odds with the rest of the industry, *has prevailed.* Utilities today are increasingly switching their units of measure to conform to the standards. Certainly this is true of GParted, which now uses KiB, MiB, and GiB as its suffixes. In the long run this will reduce confusion, albeit at the cost of users having to understand the difference between power-of-10 and power-of-2 units.

---

### Post by psusi on 2010-10-20
Yes, some utilities are moving to base 10 units.  I see no good reason to do so however, and rather than reduce confusion, it is only increasing it.  Before the only wrong or confusing number was the one from the manufacturer; everything else was in base 2.  Now some things are base 2, and some are base 10.

As for data transfer rates, bits are in base 10, bytes are in base 2.  For example, you would have a 56 kbps ( base 10 ) modem, but would download at 6 KB/s ( base 2 ).

---

### Post by srs5694 on 2010-10-21
There's *always* been a mix of base-2 and base-10 units! I was answering questions about this back in the 1990s. The big difference is that back then, the same suffixes and names were used for both, which led to at least as much confusion as there is today. The way I see it, there are three options for how to deal with this:


[list=1]
[*]Force adoption of base-10 units on everything. This has the advantage of compliance with the SI units long in use in science, industry (except in the backwards United States), etc. This has the disadvantage that using base-10 units imposes imprecision on many computer functions, many of which are better measured in base-2 units.
[*]Force adoption of base-2 units on everything computer-related, improperly using the SI suffixes for the closest available base-2 equivalent. This would require few changes in utilities (from their state a few years ago), but it's confusing to people who properly understand SI units, and it would require changes in a minority of computer units compared to past use.
[*]Adopt different names and suffixes for base-10 and base-2 units. This keeps computer and non-computer uses of SI units standardized and enables greater precision of expression, at the cost of more measurement options within the computer realm.
[/list]


The computer industry has decided to go with #3. Live with it.

---

### Post by psusi on 2010-10-21
What mix?  Who got it wrong?  The rule was bytes are in base 2.  Pretty much EVERYONE understood and abided by that, EXCEPT hard disk manufacturers.  Size of ram?  base 2.  Size of disks?  Base 2 to everyone but the HD maker.  Transfer speeds?  If given in bytes, base 2.  File size?  Base 2.

---

### Post by CharlesA on 2010-10-21
> **psusi said:**
> What mix?  Who got it wrong?  The rule was bytes are in base 2.  Pretty much EVERYONE understood and abided by that, EXCEPT hard disk manufacturers.  Size of ram?  base 2.  Size of disks?  Base 2 to everyone but the HD maker.  Transfer speeds?  If given in bytes, base 2.  File size?  Base 2.
+1. I can't really think of anything that uses base 10 to measure capacity (related to computers) except for hard drive/ssd/thumb drive manufactuers.

---

