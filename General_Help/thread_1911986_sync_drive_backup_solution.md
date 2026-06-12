---
title: "sync drive backup solution?"
date: 2012-01-19
forum: General Help
---

### Post by ulao on 2012-01-19
Hey guys I run Ubuntu 9.10 and I want to basically mirror my drive on the fly.  So that the OS makes sure both drives are identical at all times. I was wondering of ubuntu has such software?

---

### Post by Buntumatic on 2012-01-19
So when you screw up or your primary hard drive fails with filesystems corrupted the other drive gets borked, too?

---

### Post by papibe on 2012-01-19
If you are talking about user data, then the command line 'rsync' or the GUI 'Rrsync' can do just fine.

If you mean also the bootable partition, take a look at [Clonezilla]("http://clonezilla.org/").

Tell us if you need more details.
Regards.

---

### Post by ulao on 2012-01-19
LOL come-on man?   I have kback doing the back up for my files, I'm just looking for a poor mans hot swap. This is encase of a hard drive crash not a file issue.

thx papibe, that was actually a helpful post.

---

### Post by Ecip on 2012-01-19
What about a RAID1 setup?

---

### Post by Habitual on 2012-01-19
unison in the REPOs.
I can be automated via cron easily.

---

### Post by ulao on 2012-01-19
unison I found while looking for others and it wont let me copy from drive to drive. Its like it want folder on the main drive to another folder on that drive. It looks like it would work.

RAID1, looks to be used during install? the search argument is pulling up all kinds of junk any good place to read about it?

---

### Post by amigireagnobe on 2012-01-19
Hello. And Bye.  
test [test](http://www.hellojusttest.com)

---

### Post by ulao on 2012-01-20
Test: Operation not permitted, No such file or directory, No such proces...


really, what was that all about?

---

### Post by Buntumatic on 2012-01-20
You can set up RAID with mdadm utility. 

Some insight is here, make your choice [http://skrypuch.com/raid/](http://skrypuch.com/raid/)

---

### Post by ulao on 2012-01-21
I really like this mdadm, but I'm getting the feeling this only works before an install? Can I some how use this after an install? I wiped my second drive and see its usable not for mdadm but I dont see a way to select my OS drive as a source drive.

---

