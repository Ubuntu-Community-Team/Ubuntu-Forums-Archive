---
title: "Boot and Home on separate drives"
date: 2011-07-25
forum: General Help
---

### Post by Kallun on 2011-07-25
Greetings!

I'm building a new box this week, the parts are currently in the mail. I've ordered a 120GB SSD and a 1TB SATA drive. I'm looking to get the speediest system possible, so, I figured I'd have the SSD serve as a boot drive and the 1TB drive server for data.

How could I go about installing Ubuntu and having '/home' be on the 1TB drive? Is it as simple as using the installation disk and using the advanced option to specify the partition layout? As in implementing the 'use as' feature, so I'd just select the partition on my 1TB drive and select 'use as: /home' ?

Any help is greatly appreciated! :D

---

### Post by blind2314 on 2011-07-25
> **Kallun said:**
> Greetings!
 
I'm building a new box this week, the parts are currently in the mail. I've ordered a 120GB SSD and a 1TB SATA drive. I'm looking to get the speediest system possible, so, I figured I'd have the SSD serve as a boot drive and the 1TB drive server for data.
 
How could I go about installing Ubuntu and having '/home' be on the 1TB drive? Is it as simple as using the installation disk and using the advanced option to specify the partition layout? As in implementing the 'use as' feature, so I'd just select the partition on my 1TB drive and select 'use as: /home' ?
 
Any help is greatly appreciated! :D
 
 
Yup, when selecting your drives just choose the 1TB hard drive, give it one partition, and set that partition's mount point as /home. Voila.

---

### Post by Kallun on 2011-07-25
> **blind2314 said:**
> Yup, when selecting your drives just choose the 1TB hard drive, give it one partition, and set that partition's mount point as /home. Voila.

Excellent! Thanks for the swift response :)

---

### Post by oldfred on 2011-07-25
Yes you can do that.

But I like to keep each system fully functional from one hard drive and let data be on any drive. So I suggest keeping a small /home that really only has your user settings in the hidden files and have all you data on the 1TB drive.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)

Also do you really want one partition on a 1TB drive? How are you backing it up? How long will filechecks take?

I do not use Knoppix but this makes some good points:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by tomegtt on 2011-07-26
it's a good day to meet you,[microsoft office professional](http://www.professionalplus2010.com),you are a good guy and welcome to here,[Coach Bracelets](http://www.discount-coach-handbags-outlet.com/coach-bracelets-c-7.html),it's a good post good stuff.[Office 2007](http://www.office-2007-professional.com),i love it,[office 2010 online](http://www.office2010c.com)thanks for you share.Have a good  day. thanks again.

---

