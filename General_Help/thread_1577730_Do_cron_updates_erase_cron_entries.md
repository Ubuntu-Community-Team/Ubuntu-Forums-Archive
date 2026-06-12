---
title: "Do cron updates erase cron entries?"
date: 2010-09-19
forum: General Help
---

### Post by Roasted on 2010-09-19
I'm pretty darn sure I put in my cron entries to run my backup script which rsyncs my data to my 2nd drive, however on a hunch I checked my backup drive which mounts automatically via fstab and I realize it had not ran in a while. I checked cron and there were no entries for it. I got to wondering if I should ever be worried about a cron update coming down and over-writing my existing cron file with the backup entries in it to run. Any input?

---

### Post by llamabr on 2010-09-19
Nope.  An update, updates the package, which is located in /usr/sbin/  Your jobs are located in /etc/cron*

Just put it back, and you'll be fine.  But you're right to check it now and again.  Things happen.

---

### Post by Roasted on 2010-09-20
> **llamabr said:**
> Nope.  An update, updates the package, which is located in /usr/sbin/  Your jobs are located in /etc/cron*

Just put it back, and you'll be fine.  But you're right to check it now and again.  Things happen.

That's what I did, and things are good now. I had to reformat a while back when I did something mucho bad with my install. I forget what I did but I just redid it. I thought I restored the file server side of it pretty quickly though, which is where I have drives shared out with certain user permissions and the rsync script backs the data up to a 2nd drive in the system for redundancy... but hey maybe I missed it. I just wanted to take the time to ask and be sure instead of being naive and not knowing something that is pretty critical in this case...

---

