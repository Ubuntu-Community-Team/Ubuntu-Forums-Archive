---
title: "Extremely erratic RAID 5 performance."
date: 2011-07-16
forum: General Help
---

### Post by jmail524 on 2011-07-16
Hi everyone,

Once again I call on the gurus of Linux to explain this one...

I built a RAID5 storage array using 'mdadm' on 3x WD Green 1TB hard drives.  I used the Disk Utility GUI to create the array and it took about 24 hours to build.  When I started copying files to it I noticed it performed at decent speeds for a while, then got really slow, the sped back up.  Just for laughs I ran the Read-Only Benchmark function in the Disk Utility and got a graph that would even confuse stock brokers.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197639&stc=1&d=1310874255[/IMG]

Any thought on what the issue might be?  I tried searching around for an answer, but most people are only affected by wirte performance issues not reading.  Any help is greatly appreciated.

Thanks.
Brian

---

### Post by coffee412 on 2011-07-16
> **jmail524 said:**
> Hi everyone,
(edited)
Any thought on what the issue might be?  I tried searching around for an answer, but most people are only affected by wirte performance issues not reading.  Any help is greatly appreciated.

Thanks.
Brian

As the drives are righting data to the drive they also have to store info about the data. Perhaps it just bogging down on writing the extra data. My raid5 with 4 drives does it as its writting to the drives. 

Just my thoughts....

---

### Post by dcstar on 2011-07-17
> **jmail524 said:**
> Hi everyone,

Once again I call on the gurus of Linux to explain this one...

I built a RAID5 storage array using 'mdadm' on 3x WD Green 1TB hard drives.
.........

I have read issues with those particular drives where their inbuilt spindown timers are shorter than the Linux kernel flush times.

Apparently this means that the drives are continually shutting down to save power then been woken up a couple of seconds later - which takes time as these drives spin up slower than normal drives as part of their power saving features.

You might want to check the SMART attributes in the Disk Manager to see if there are abnormally high counts for spinups etc.

---

### Post by jmail524 on 2011-07-17
Thanks for the speedy replies...

The read and write performance appear to be very close to each other and seem to exibit the same pauses during transfers.

I understand that these are not optimal drives for a RAID environment.  It's what I had laying around and thought I build a quick RAID setup to help protect some of my data from a simple drive failure.

I checked the SMART status through Disk Utility.  All three of the drives had 170 for the "Start Stop Count" value.  This was about half of the rest of the drives in my machine, although these drives had a much different life.  (They were originally used in a 24/7 media server for about 2 years.)

Is there any merit in attempting to change the flush time of the kernel? (I don't even know if there is a setting for that.) I currently have a 1MB stripe size.  Would selecting a smaller stripe be adventageous with these particular drives? (I don't know if stripe size and flush function have any correlation to each other.)

Thanks for the suggestions.  I look forward to more great ideas on this issue.
Brian

---

### Post by jmail524 on 2011-07-20
I tried creating the RAID array with different stripe sizes and it did make a difference.

Originally with a 1MB stripe:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197639&stc=1&d=1310874255[/IMG]

Now with a 512KB stripe:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197910&stc=1&d=1311202533[/IMG]

Finally a 256KB stripe:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197911&stc=1&d=1311202533[/IMG]

In my particular case, it appears that the maximum stripe size does not warrant the best performance.  I suppose, because these are only 5400rpm drives, there is too much data being pushed on the drive at one time with the 1MB stripe size. I am happy with the performance of the 512KB stripe and will stick to it and hope it cured my stuttering issue. (So far so good.)

Thanks for everyone's input.
Brian

---

### Post by nipennem on 2011-07-31
I doubt the palimpsest (disk utility) benchmarks will be influenced by the idle timer of your WD disks.

However, you might be able to increase the performance of your array and the lifetime of your disks slightly by using a tool to change your idle timer's timeout value, but **this will void your warranty.**

Instructions and download on 
[http://www.synology.com/support/faq_show.php?q_id=407]("http://www.synology.com/support/faq_show.php?q_id=407")

Did you mean **chunk or striDe** size instead of **stripe** size? Palimpsest benchmarks the raw performance of a device, not a filesystem. The chunk or stride size is a parameter of the array device, the stripe width is a parameter of the filesystem(s) you create on top of it and should be tuned to match the parameters of the array. Hence, the stripe size cannot impact your benchmarks. To benchmark filesystem performance, use bonnie++.

---

### Post by ziggo0 on 2012-01-19
> **nipennem said:**
> I doubt the palimpsest (disk utility) benchmarks will be influenced by the idle timer of your WD disks.

However, you might be able to increase the performance of your array and the lifetime of your disks slightly by using a tool to change your idle timer's timeout value, but **this will void your warranty.**

Instructions and download on 
[http://www.synology.com/support/faq_show.php?q_id=407](http://www.synology.com/support/faq_show.php?q_id=407)

Did you mean **chunk or striDe** size instead of **stripe** size? Palimpsest benchmarks the raw performance of a device, not a filesystem. The chunk or stride size is a parameter of the array device, the stripe width is a parameter of the filesystem(s) you create on top of it and should be tuned to match the parameters of the array. Hence, the stripe size cannot impact your benchmarks. To benchmark filesystem performance, use bonnie++.

I know this will be considered digging up a dead thread, but disabling the idle timer or changing it's value **_DOES NOT VOID YOUR WARRANTY!!!**_. I've RMA'd many WD Green drives (EACS, EADS & EARS) of multiple sizes internal and external with all their idle timers disabled and have had no issue. I've ever spoken to WD about this and they said it is not a problem.

---

