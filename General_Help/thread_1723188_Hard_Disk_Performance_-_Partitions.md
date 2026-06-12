---
title: "Hard Disk Performance - Partitions"
date: 2011-04-06
forum: General Help
---

### Post by oldskool on 2011-04-06
Ubuntu 10.10 is dual booted but it is my primary OS. 

Unfortunately it's on the outer edges of the disk in an extended partition. 

This has always bugged me, with regards to read/write performance. 

Do my concerns of reduced performance have any foundation? Should i bite the bullet and format the drive installing ubuntu first? 

I ran the disk read benchmark and my read speeds were 100MB/Sec at the beginning of the test to just 55MB/Sec at the end. I have no idea if the position of the test has any bearing on the position of the disk or whether the speed recorded is affected by other factors such as the tests function or simulation. 

I would really appreciate some guidance on disk performance, specifically, whether it is worth formatting and re-installing. 

Thanks,

---

### Post by grahammechanical on 2011-04-06
Here you are, study this. Look at performance characteristics - seek time, access time, latency, data transfer rate.

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)

By the way, do not think of installing Ubuntu first and then installing Windows. You will have lots of problems as Microsoft believes that its operating systems are the only ones that should be installed on a computer hard disk.

Regards.

---

### Post by techunit on 2011-04-06
Drives don't really work that way. You should always defragment a partition before you resize it. That really only applies to windows which has a sloppy file system. So before you you shrink partitions you can make sure that it is going to work better by doing so.

To answer you question. No you will only mess up your computer. Installing Ubuntu first before windows is only a headache You would be better off formating and only using Ubuntu. You might be able to run the same windows that came with the machine in a VM like Virtualbox.

---

### Post by srs5694 on 2011-04-07
"First" can mean two things in this context:


[list]
[*]Temporally -- If you install Ubuntu at 10:00 AM and Windows at 11:00 AM, then Ubuntu was installed first.
[*]Sector use -- If Ubuntu is installed starting at sector 2048 and Windows starts at sector 470,177,792, the Ubuntu is installed first.
[/list]


These two meanings are independent; Ubuntu could be installed first by sector use, but second temporally, or vice-versa. Clearly, oldskool was referring to sector use first installation of Ubuntu; but grahammechanical and techunit were both warning against temporal first installation of Ubuntu.

As to the original question, it's entirely possible that Ubuntu's performance is suffering by it being at the end of the disk; however, this effect is likely to be fairly small in real-world terms, since lots of factors besides raw disk throughput affect performance. (For instance, head seek time, CPU speed, bus speed, etc.) When you balance the performance gains from juggling your partitions around against the time spent in doing this and the risks involved, IMHO it's probably not worth the effort. An exception might be if you were doing some *very* disk-intensive tasks, like running a major database server or doing disk-intensive scientific simulations. You'd probably want a RAID array or an SSD drive for such a computer, though.

---

### Post by lithopsian on 2011-04-07
It doesn't matter which you install "first".  Format the drive any way you like and then install each OS to the partitions where you want.  Personally I don't think you'll see a massive difference.  We are in the 21st century now and this sort of performance tip was important 30 years ago.  Now, for most applications, seek time tends to be the limiting factor.  Linux file systems are particularly sparse and they scatter their files all over whatever partition they have, although they are pretty good at keeping individual files intact.  Just possibly when you are using a utility like readahead during Ubuntu boot you might get close to theoretical transfer limits.  A lot depends on your hardware, caching, SATA/PATA, and other details.  You can use bootchart to see what sort of data transfer speeds you are getting during boot and then decide whether it is likely to be improved by moving the partition.

---

### Post by oldskool on 2011-04-07
Thank you all for the excellent advice. 

Nothing intensive going on. Just marvelling at the excellent performance of Ubuntu since switching from Windows. Would hate to think it is stifled by living in the outer sectors of the disk. I admit my knowledge is from the days of running the first iterations of Pentium processors and 8gb hard drives. I appreciate seek times, caching and data rates have significantly improved since then.  

In reality the performance is probably reduced, by how much; potentially indistinguishable for what I do. I move large data files around less than < 5% of the time and my usage rarely involves multiple file access or transfer. 

As advised, no need to rush into a format. 

Many thanks,

---

