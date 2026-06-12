---
title: "Need help in cloning HDD"
date: 2011-12-29
forum: General Help
---

### Post by ashwinrao on 2011-12-29
I have 2 500 GB HDD's. One is Seagate(sda) and another is WD (sdb). I'm currently using WD with Win7 and Ubuntu 11.10. I wish to clone this HDD image to my new Seagate 500 GB HDD. Output of sudo fdisk -l is:
```
:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b19ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   104326109    52163023+   7  HPFS/NTFS/exFAT
/dev/sdb2       104326110   413561294   154617592+   7  HPFS/NTFS/exFAT
/dev/sdb3       413561295   679806539   133122622+   7  HPFS/NTFS/exFAT
/dev/sdb4       679806601   976769023   148481211+   5  Extended
/dev/sdb5       679806603   875124809    97659103+   7  HPFS/NTFS/exFAT
/dev/sdb6       894740480   898643967     1951744   82  Linux swap / Solaris
/dev/sdb7       875126784   894738431     9805824   83  Linux
/dev/sdb8       898646016   976769023    39061504   83  Linux

Partition table entries are not in disk order
```

Please guide me through this process.

---

### Post by alphaamanitin on 2011-12-29
[LEFT][FONT=Arial][SIZE=2]> **ashwinrao said:**
> I have 2 500 GB HDD's. One is Seagate(sda) and another is WD (sdb). I'm currently using WD with Win7 and Ubuntu 11.10. I wish to clone this HDD image to my new Seagate 500 GB HDD. Output of sudo fdisk -l is:
```
:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b19ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   104326109    52163023+   7  HPFS/NTFS/exFAT
/dev/sdb2       104326110   413561294   154617592+   7  HPFS/NTFS/exFAT
/dev/sdb3       413561295   679806539   133122622+   7  HPFS/NTFS/exFAT
/dev/sdb4       679806601   976769023   148481211+   5  Extended
/dev/sdb5       679806603   875124809    97659103+   7  HPFS/NTFS/exFAT
/dev/sdb6       894740480   898643967     1951744   82  Linux swap / Solaris
/dev/sdb7       875126784   894738431     9805824   83  Linux
/dev/sdb8       898646016   976769023    39061504   83  Linux

Partition table entries are not in disk order
```Please guide me through this process.


I assume sda is the new seagate drive, given that sda is empty. I guess you want to clone sdb to sda.  Here is how it is done through the command line.  Suggest you use a computer with at least 4 gb of ram.  

This should be done from a liveCD of ubuntu (I find it faster if you use a USB drive with ubuntu on it).

```
sudo dd if=/dev/sdb of=/dev/sda bs=32M conv=notrunc,noerror
```  "if"means input file, "of" means output file **[COLOR=red]NEVER CONFUSE THESE OR YOU JUST LOST EVERYTHING YOU WANTED TO CLONE!!!!!![/COLOR]**  You can check progress with the following command (run this command in a new terminal window):[/SIZE][/FONT]```
[FONT=Arial][SIZE=2]pgrep -l '^dd$'[/SIZE][/FONT]
```[FONT=Arial][SIZE=2] this will give you the ID code (the number in the output), then run this command:[/SIZE][/FONT]```
[FONT=Arial][SIZE=2]kill -USR1  XXXXX[/SIZE][/FONT]
```[FONT=Arial][SIZE=2]

Use the number from the pgrep out put in place of those XXXXX.  In the original window that the dd command was run from it will output the amount of copied bytes.  When the command is finished it will output more info in the same fashion as the kill command.  

Don't do this until you are 100% sure exactly what you are doing, what is going to happen, and that you have everything set up correctly.  If you mess it up you can/will lose everything.

AlphaA
[/SIZE][/FONT][/LEFT]

---

### Post by jerrrys on 2011-12-29
I prefer a GUI

 [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by ashwinrao on 2011-12-30
Thanks a lot for your replies [alphaamanitin]("http://ubuntuforums.org/member.php?u=952078") and [jerrrys]("http://ubuntuforums.org/member.php?u=718079"). I prefer command line as I'm Linux newbie and wish to learn by my own mistakes. Started work as suggested by [alphaamanitin]("http://ubuntuforums.org/member.php?u=952078") . I believe, the commands 'pgrep -l '^dd$'' and 'kill -USR1  XXXXX' not must to run right? Please correct me if I'm wrong.

---

### Post by Paqman on 2011-12-30
I wouldn't recommend using dd for cloning disks. It will copy every bit including empty space, which means you'd potentially be wasting an awful lot of time on a large disk such as this. It's also potentially a very dangerous command if you mess it up (which we all do occasionally)

+1 for Clonezilla instead. Faster, safer, easier to use.

---

### Post by kurja on 2011-12-30
> **Paqman said:**
> I wouldn't recommend using dd for cloning disks. It will copy every bit including empty space, which means you'd potentially be wasting an awful lot of time on a large disk such as this. It's also potentially a very dangerous command if you mess it up (which we all do occasionally)

+1 for Clonezilla instead. Faster, safer, easier to use.

Or if it's just a storage disk you might as well drag and drop everything.

If it's a bootable drive then dd more or less guarantees that the clone will work when set up in the original's place, correct? Would clonezilla achieve the same?

---

### Post by Paqman on 2011-12-30
> **kurja said:**
> Would clonezilla achieve the same?

Yes, it can clone an entire drive, including MBR. Or it can be used to clone individual partitions, make backups, etc. It's very flexible.

---

### Post by ashwinrao on 2011-12-30
Thanks every one for your guidance. I've used 'dd' command and now I'm working from new HDD. I've used this method since I didn't wish to loose my primary OS Ubuntu installation. I'm not concerned about other OS and the data. However, one issue remains now. My Disk Utility displays: ```
WARNING: The partition is misaligned by XXX bytes. This may result in very poor performance. Repartitioning is suggested.
```

Is this common while using 'dd' command? Also, can it be ignored?

---

### Post by jerrrys on 2011-12-30
I have not had this problem, but found this:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partition+is+misaligned&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partition+is+misaligned&sa=Search&cof=FORID:9)

---

### Post by alphaamanitin on 2011-12-30
I have cloned about 5 or 6 drives now and never had that problem.  I wouldn't worry too much thought because you can retry or use other methods to clone the WD to seagate.  Just make sure that neither drive is actively being used at the time to minimize any risk of damage or errors.

AlphaA

---

### Post by ashwinrao on 2011-12-30
Thank you AlphaA and jerrrys for your assistance. I'll backup my data and repartition the disk some other day. I'll mark this thread as resolved as I've successfully copied the OS and they are working fine. Thanks again for you all!

---

