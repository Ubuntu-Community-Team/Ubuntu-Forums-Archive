---
title: "Help with smartmontools - failing drive?"
date: 2012-09-03
forum: General Help
---

### Post by Oddity on 2012-09-03
My entire system suddenly went read-only on me, and then it refused to boot up. I used a live CD to mount my partitions and backup some files and got multiple cases of:

File shrank by xxxxxxx bytes; padding with zeros

and

Cannot stat: Input/output error

I then installed smartmontools with GSmartControl, but I'm unsure how to interpret the result:

[[img]http://s18.postimage.org/5jmmdcpet/Attributes.jpg[/img]](http://postimage.org/image/5jmmdcpet/)

I have attached the error log as well.



So now my question is: Should I be worried?

---

### Post by gordintoronto on 2012-09-04
My preference is to use Disk Utility, click on the drive and look at the Smart data.

Yes, you should be very worried about this drive! How is your backup?

---

### Post by 2F4U on 2012-09-04
As I interpret the output of the log you have bad sectors on the hdd. These are already affecting existing data on the drive and it is likely that the amount of bad sectors increases, affecting even more of your data.

---

### Post by Oddity on 2012-09-04
Thanks everyone!

My backup should be good - got a copy of the entire home dir on an external drive, and my critical stuff is in any case in Dropbox.

Better go shopping for a new internal drive, then! :-|

---

### Post by gordintoronto on 2012-09-05
You should be proud of yourself for having backup. All too often we see, "but how can I get back all my family photos from the past decade?"

---

