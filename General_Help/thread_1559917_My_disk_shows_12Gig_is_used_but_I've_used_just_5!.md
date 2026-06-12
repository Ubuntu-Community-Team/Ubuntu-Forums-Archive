---
title: "My disk shows 12Gig is used but I've used just 5!"
date: 2010-08-24
forum: General Help
---

### Post by Ve5ahchoo8ah on 2010-08-24
hi
I have a 20Gig space for ubuntu. I installed it by wubi (which i regret now!)
my disk shows that 12.5Gig is used but when I use Disk Usage Analyzer, it shows that there is just 4.7Gig used!
If you look at the picture you'll get me
What does it mean?! Where is my hard space?
(btw: is there any way to move from wubi to a real install? or change wubi space)

---

### Post by Ve5ahchoo8ah on 2010-08-24
sorry but there most be an explanation! :(

---

### Post by cdnwolverine on 2010-08-24
Are you running Disk Usage Analyzer as root? If not, there's likely parts on the drive that your account doesn't have access to and is unable to tally those files.

On top of that, the ext3 file system saves about 5% of the disk for just root so your users won't be able to fill up the drive and cause related issues .. unless you do it as the root user, of course.

---

### Post by Ve5ahchoo8ah on 2010-08-25
YES! that was the answer! thank you very much
(and I found out that my backups are using most of my disk!)

---

