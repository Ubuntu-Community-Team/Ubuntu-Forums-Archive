---
title: "corrupted FAT: howto recover lost files"
date: 2006-04-05
forum: General Help
---

### Post by DFreeze on 2006-04-05
I’ve recently used GParted to fix the FAT of a failing drive (“unable to read superblock” or something like that). Problem is: I just parked 30 GB of files on that disk to free another.

So now the disk is mounted without problems, but the data is invisible, off course. Are there (open source / free) tools for recovering the data? I haven’t used the disk since, so everything should still be there…

Could you give me names of packages / programs and maybe a howto on the matter?

---

### Post by frodon on 2006-04-05
Try ddrescue, if one open source tool can do something for you it's surely ddrescue it helped me at the time when my hdd crashed.
First install it, it's in the repositories then you will find instruction on how to use it here : [http://www.titov.net/category/server-administration/](http://www.titov.net/category/server-administration/).
So reboot your computer without mounting your harddrive and then run this command to create the image file (it will take a huge time maybe 15-20 hours) : ```
dd_rescue /dev/name_of_device /home/*username*/drive-img
```Then read the link i gave you (see the second topic) to know how to mount this image file.

---

### Post by DFreeze on 2006-04-05
So, this tool can recognise which parts of the disksurface were files or folders? Because I can mount the disk now, its just that the information in the FAT-table about where the files are at, is lost. The data is still on it, but its just not allocated anymore.

---

### Post by frodon on 2006-04-05
This tool is made to rescue datas on corrupted partitions so i think it is able to read the datas even if the partition table is lost. Anyway running ddrescue will not mess up your datas so you should give it a try i think.
If it don't work you could also try recoverdm : [http://www.vanheusden.com/recoverdm/](http://www.vanheusden.com/recoverdm/)

Let us know if one of those tools helped you.

---

### Post by az on 2006-04-05
foremost works great at finding lost files

[http://packages.ubuntu.com/breezy/admin/foremost](http://packages.ubuntu.com/breezy/admin/foremost)

Can you make an image of the drive first?  Do you have enough disk space somewhere else?

---

### Post by nisarg on 2008-03-07
Recently my laptop crashed and found that the HDD was the problem most likely bad sectors. My PC wont boot anymore. 
I ran Ubuntu Live CD 7.10 Gutsy and tried to copy the data over to another drive. But it does not work. It fails to copy the data and terminates to process. Copying around 40gigs using the CP command, and on a couple of occasions it all went haywire when it hit an error or something. 
So I setup Samba on it, and mounted a network drive. 
Installed ddrescue and started to copy data using the following command:

$ sudo ddrescue -r 3 /home/Backup/backup.img /home/Backup/Backup.log

I started this 4 days back, and have to say was quite impressed with its copying rate when it started. Over night it has dropped and now after 4 days it has really turned into a slug..
Heres what it looks like currently.

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:    35811 MB,  errsize:    151 MB,  current rate:     4327 B/s
   ipos:    35963 MB,   errors:    4296,    average rate:     144 kB/s
   opos:    35963 MB
Copying data...
 
At times it dropped below 200 B/s. 
I would like to ask:

-Is this normal with ddrescue?
-Does it take weeks to rescue a 60gb disk?
-Is the no. of retries I have specified causing a slow down? I would imagine so.
-I know ddrescue can be stopped and restarted. But kind of scared to loose everything and start again.
-Any suggestions what can I do to speed it up?
-Does this mean my drive is really screwed up? 

BTW:
here are the details from fdisk -l  
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34593cce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS

All inputs appreciated.

Cheers, N

---

### Post by zazuge on 2008-05-16
testdisk recover lost partitions
and photorec recover files by headers
it recognize lots of MiMe tyep (even 7z rar ...)
hope that helps

---

