---
title: "why more space free than available? I'm going crazy!"
date: 2010-05-12
forum: General Help
---

### Post by capuccino on 2010-05-12
Hi, I dont know what to do guys :confused:

why do I have more space free than available? I did some research on the forum but I didnt find something about this

on the home partition I have 3.9Gb free space but only has 964Mb available, do you have any ideas what it could be?


cheers and thanks!

---

### Post by ibuclaw on 2010-05-12
Where, What and Who are you getting this information from?

---

### Post by kerry_s on 2010-05-12
where you getting the numbers from?

---

### Post by a-user on 2010-05-12
how big is your home partition? it seems it cause of the reserved root space. default is 5% of the size is reserved for root. hence probalby 3GB are resvered for root thus 900MB are available.

---

### Post by ibuclaw on 2010-05-12
> **a-user said:**
> how big is your home partition? it seems it cause of the reserved root space. default is 5% of the size is reserved for root. hence probalby 3GB are resvered for root thus 900MB are available.

That "reserve root space" is called the File system Journal, and it's size is usually omitted from disk usage / reporting utilities.

---

### Post by capuccino on 2010-05-12
Hi

Im getting this info from the System Monitor. here is a pic. do you think this is normal? there is something I could do?

thanks!


Ps. I forgot to say that Im receiving low disk space warnings


[IMG]http://img39.imageshack.us/img39/8828/screenshotya.jpg[/IMG]

---

### Post by srs5694 on 2010-05-12
> **ibuclaw said:**
> That "reserve root space" is called the File system Journal, and it's size is usually omitted from disk usage / reporting utilities.

I'm afraid you're confusing two things:


[list]
[*]The ext2/3/4 filesystems reserve a certain amount of free space for root. This value defaults to 5%, but it can be set to other values, either at filesystem creation time or using tune2fs, using the -m or -r parameter. (The tune2fs man page refers to this space as the "reserved blocks percentage" or "reserved blocks count," depending on how it's measured.) The reason for reserving space is to give root the ability to log in and deal with problems should ordinary users fill up a disk.
[*]The filesystem journal is a data structure that stores information on what parts of the disk are being operated upon. The idea is that, in the event of a power failure, system crash, or other uncontrolled shutdown of the disk, the journal can be used to direct the disk check operation when the system starts up again. Without the journal, the whole disk must be checked, but with the journal, only those areas that are flagged as being in use need to be checked.
[/list]


Whether these figures are included or omitted in filesystem space estimates depends on the utilities involved. The screen shot provided by capuccino indicates that a single utility provided two contradictory estimates that varied on these measures:

57.8GB total space, multiplied by 0.95, yields 54.91GB; subtract 53.9GB used and you get 1.01GB, which is still a bit more than the 964.9MB "available." A journal could account for the remaining difference. So might slop in disk allocation. For instance, if disk space is allocated in 4KB blocks, and if a file is 10KB in size, it will take three blocks to store, so a 10KB file will occupy 12KB of disk space. Add up those differences and you can get into large amounts of disk space. The extent of this effect varies depending on the filesystem and the sizes of the files stored in it.

In any event, the bulk of the effect observed by capuccino is almost certainly a result of the 5% reserved space. Since this is a /home partition, it's safe to reduce the reserved space. This can be done by typing the following command at a text-mode shell prompt:

```

sudo tune2fs -m 0 /dev/sda3

```

If you wanted to leave some reserved space, you could change the value from 0 to 1; however, I don't think this is necessary, since root shouldn't need to create files in /home to restore the system should the disk fill up.

---

### Post by a-user on 2010-05-12
> **ibuclaw said:**
> That "reserve root space" is called the File system Journal, and it's size is usually omitted from disk usage / reporting utilities.
no, you are totally wrong. filesystem journal is something totaly different to the root reserved space. srs5694 explained it in details.

and the space reserved is usually not substracted from the free space. for this you have the available tag. this explains your issue most probably.

EDIT: there is another possibility. is your trash empty?

EDIT2: @[srs5694]("http://ubuntu-ky.ubuntuforums.org/member.php?u=1032238"): you are partially wrong with the root reserved space. this is not a FS specific thing. its not only with extx. linux distributions do this usually no matter what fs you are using, be it xfs jfs, ext or harekrishna. they reserv scapce for the root user in case some dumb programm or user had filled up the whole space so that root can still operate fixing things or similar stuff.

---

### Post by ibuclaw on 2010-05-12
> **srs5694 said:**
> I'm afraid you're confusing two things:


[list]
[*]The ext2/3/4 filesystems reserve a certain amount of free space for root. This value defaults to 5%, but it can be set to other values, either at filesystem creation time or using tune2fs, using the -m or -r parameter. (The tune2fs man page refers to this space as the "reserved blocks percentage" or "reserved blocks count," depending on how it's measured.) The reason for reserving space is to give root the ability to log in and deal with problems should ordinary users fill up a disk.
[/list]


Was never aware there was such a distinction. I guess I always assumed that 5% reserved space was for the journal. That's nice to know, thanks. :P

---

### Post by srs5694 on 2010-05-12
> **a-user said:**
> EDIT2: @[srs5694]("http://ubuntu-ky.ubuntuforums.org/member.php?u=1032238"): you are partially wrong with the root reserved space. this is not a FS specific thing. its not only with extx. linux distributions do this usually no matter what fs you are using, be it xfs jfs, ext or harekrishna. they reserv scapce for the root user in case some dumb programm or user had filled up the whole space so that root can still operate fixing things or similar stuff.

AFAIK, it's ext2/3/4-specific. Certainly it's not true of ReiserFS or XFS. I just tested this with a small partition, using ext2fs, ReiserFS, and XFS. With ext2fs:

```

$ **dd if=/dev/zero of=/mnt/usb/zero.img**
dd: writing to `/mnt/usb/zero.img': No space left on device
101083+0 records in
101082+0 records out
51753984 bytes (52 MB) copied, 0.408887 s, 127 MB/s
$ **df -h /mnt/usb**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1                54416     51630         0 100% /mnt/usb
$ **sudo dd if=/dev/zero of=/mnt/usb/root-zero.img**
dd: writing to `/mnt/usb/root-zero.img': No space left on device
5549+0 records in
5548+0 records out
2840576 bytes (2.8 MB) copied, 0.0213517 s, 133 MB/s
$ **df /mnt/usb**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1                54416     54416         0 100% /mnt/usb
$ **ls -l /mnt/usb**
total 53538
drwx------ 2 root     root     12288 May 12 10:52 lost+found
-rw-r--r-- 1 root     root   2840576 May 12 10:54 root-zero.img
-rw-r--r-- 1 rodsmith users 51753984 May 12 10:53 zero.img

```

Note the differences in the df output after user and root (sudo) dd copies, and note that the root (sudo) dd resulted in 5548 records output, and note the sizes of the files that resulted. Now the same thing, with XFS:

```

$ **dd if=/dev/zero of=/mnt/usb/zero.img**
dd: writing to `/mnt/usb/zero.img': No space left on device
96945+0 records in
96944+0 records out
49635328 bytes (50 MB) copied, 9.09751 s, 5.5 MB/s
$ **df /mnt/usb**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1                51396     51376        20 100% /mnt/usb
$ **sudo dd if=/dev/zero of=/mnt/usb/root-zero.img**
dd: writing to `/mnt/usb/root-zero.img': No space left on device
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00716467 s, 0.0 kB/s
$ **df /mnt/usb**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1                51396     51376        20 100% /mnt/usb
$ **ls -l /mnt/usb**
total 48472
-rw-r--r-- 1 root     root         0 May 12 10:58 root-zero.img
-rw-r--r-- 1 rodsmith users 49635328 May 12 10:58 zero.img

```

Note that "dd" showed all but 20 blocks were used by the ordinary user, and those blocks weren't usable by root, either. (Maybe they're reserved for directories or something.) The root (sudo) dd operation resulted in 0 records output, and the root file is 0 bytes in size. ReiserFS shows similar patterns to those of XFS, although in its case, root can't even create a 0-size file.

I haven't tested JFS or Btrfs, but I'm pretty sure I recall JFS being like XFS and ReiserFS. I've not looked into the issue for Btrfs.

As I said, you can adjust the amount of reserved space with an ext2/3/4-specific tool, tune2fs.

---

### Post by a-user on 2010-05-17
@[srs5694]("http://ubuntuforums.org/member.php?u=1032238"):
i did not tested this on ubuntu but some years ago i had reiser on a suse machine and i did had the 5% root reservation there. i also had it with xfs. it could be that this reservation bound is differently implemented by the fs-system hence the differences with dd.

i dont know the details but i definitly had 5% root reservetion also on other than ext fs partitions.

---

### Post by iponeverything on 2010-05-17
I always drop my reserved from 5%  -- 5% of 1 TB drive is 51.2 gigs! way, way too much.

---

### Post by srs5694 on 2010-05-17
> **a-user said:**
> @[srs5694]("http://ubuntuforums.org/member.php?u=1032238"):
i did not tested this on ubuntu but some years ago i had reiser on a suse machine and i did had the 5% root reservation there. i also had it with xfs. it could be that this reservation bound is differently implemented by the fs-system hence the differences with dd.

i dont know the details but i definitly had 5% root reservetion also on other than ext fs partitions.

I've *never* seen this, or even heard of it, in ReiserFS or XFS. There's no mention of any reserved space option in either the mkreiserfs or the mkfs.xfs man page. My previous post demonstrated that it is *not* present in XFS (or ReiserFS; I didn't post the results, but as I said, I did run the test) using default filesystem creation options. The simplest conclusion is therefore that you're mistaken. If you care to produce documentation or experimental evidence to the contrary, please post it.

---

