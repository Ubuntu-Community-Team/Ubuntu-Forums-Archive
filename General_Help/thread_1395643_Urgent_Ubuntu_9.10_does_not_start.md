---
title: "Urgent: Ubuntu 9.10 does not start"
date: 2010-02-01
forum: General Help
---

### Post by argnur on 2010-02-01
Hello guys,
Problem with Ubuntu 9.10 on HP Pavilion dv2700.
For the last 2 days my ubuntu does not start properly, or rather does not start at all! And I have no clue what the problem is. I am eternally grateful for any help in advance!
Here is the chronology:
1) I was surfing the net
2) The screen started blinking and the laptop locked up
3) Ubuntu did not start properly any more
4) Screen displays malformed ugly texts and symbols when booting and it got split into 6 parts.
Please have a look at the attached pictures
Other info:
1)Sometimes computer starts properly (1 in 100 times) but locks up after 1 minute of use
2)I have had a few lockups after upgrading from 9.04 to 9.10. For ex. when plugging in a projector.
Please, please help!

---

### Post by JohnyN on 2010-02-01
I think it's a hardware problem.

---

### Post by realzippy on 2010-02-01
> **JohnyN said:**
> I think it's a hardware problem.

Don't think so.There were certain threads about the "6 screens bug" in the last weeks...e.g. here:

[http://ubuntuforums.org/showthread.php?t=1284017](http://ubuntuforums.org/showthread.php?t=1284017)

..solved by a modeline and some other xorg.conf modifications.

---

### Post by timgood on 2010-02-01
I also think it is a hardware problem as the BIOS screen has the same problem, long before X or any video drivers are loaded.

---

### Post by Rhubarb on 2010-02-01
While I tend to believe it may be a hardware problem, it may just possibly be because your laptop thinks there is a projector plugged into it, so it's trying to display a different resolution out-of-sync image on your laptop screen.

I would try: plugging the projector in and out of the laptop after several combinations (projector plugged into laptop, then bootup laptop, see if you can see anything on projector or laptop screen).

If you can, try to reset your CMOS (reset your BIOS back to default settings).

Otherwise, if your laptop is still under warranty, get it booked in for a service.

---

