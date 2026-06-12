---
title: "My hard drive has shrunk"
date: 2011-03-10
forum: General Help
---

### Post by juliancam on 2011-03-10
I decided to swap my existing small hard drive for a bigger one  which went well. Then I formatted the old drive using a windows vista machine before putting it on my spares shelf. To my amazement after formatting my 20GB hard drive had become an 8GB hard drive. I fear the worst but remember that Ubuntu put a large swap file on the drive and wonder if Vista has just ignored the system partition. I tried attaching it to my Ubuntu laptop which reports a healthy 8GB hard drive even after formatting again. I don't know enough about Ubuntu to try repartitioning it in that so I tried DSKCHK in windows which reported a healthy 8 GB hard drive. Is all hope lost or is it a "hidden" partition which might be recovered under Ubuntu? If so, how?

any help gratefully received

Julian

---

### Post by juliancam on 2011-03-10
OOOPs how did this get into the Apple subsection. Please Ignore.  I have moved it to the correct forum

Julian

---

### Post by juliancam on 2011-03-10
I decided to swap my existing small hard drive for a bigger one   which went well. Then I formatted the old drive using a windows vista  machine before putting it on my spares shelf. To my amazement after  formatting my 20GB hard drive had become an 8GB hard drive. I fear the  worst but remember that Ubuntu put a large swap file on the drive and  wonder if Vista has just ignored the system partition. I tried attaching  it to my Ubuntu laptop which reports a healthy 8GB hard drive even  after formatting again. I don't know enough about Ubuntu to try  repartitioning it in that so I tried DSKCHK in windows which reported a  healthy 8 GB hard drive. Is all hope lost or is it a "hidden" partition  which might be recovered under Ubuntu? If so, how?

All help gratefully received

Julian

---

### Post by slooksterpsv on 2011-03-10
> **juliancam said:**
> I decided to swap my existing small hard drive for a bigger one   which went well. Then I formatted the old drive using a windows vista  machine before putting it on my spares shelf. To my amazement after  formatting my 20GB hard drive had become an 8GB hard drive. I fear the  worst but remember that Ubuntu put a large swap file on the drive and  wonder if Vista has just ignored the system partition. I tried attaching  it to my Ubuntu laptop which reports a healthy 8GB hard drive even  after formatting again. I don't know enough about Ubuntu to try  repartitioning it in that so I tried DSKCHK in windows which reported a  healthy 8 GB hard drive. Is all hope lost or is it a "hidden" partition  which might be recovered under Ubuntu? If so, how?

All help gratefully received

Julian

To see if there's other unused partitions either use:
Ubuntu - gparted - Available from Software Center
Windows - diskmgmt.msc - Type in on run, or start search

That will show you the partitions, and if there's any hidden. Formatting just clears data and sets up the MFT and what not. Partitioning creates sections/segments.

---

