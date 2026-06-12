---
title: "Imaging?"
date: 2010-11-03
forum: General Help
---

### Post by Yezinki on 2010-11-03
Which are the recommended apps to create & restore Full Back Up Images of a machine.........like ATI Home for windows?

Can ATI Home 2011 create & restore full back up images of both Linux based & ntfs windows?

---

### Post by matt_symes on 2010-11-03
Hi

Clonezilla, remastersys or the dd command.

Sorry no idea about ATI home 2011.

Kind regards

---

### Post by MartyBuntu on 2010-11-03
> **Yezinki said:**
> Which are the recommended apps to create & restore Full Back Up Images of a machine.........like ATI Home for windows?

Can ATI Home 2011 create & restore full back up images of both Linux based & ntfs windows?


I use ATI for my backups, but understand that currently Acronis cannot work
properly with **ext4** filesystems. That is why I am still using **ext3** when doing Ubuntu installs.
Acronis claims they will accommodate **ext4** in future builds.

---

### Post by Yezinki on 2010-11-03
Thanks for your replies.

Which version of Clonezilla?

---

### Post by matt_symes on 2010-11-03
Hi

[http://clonezilla.org/](http://clonezilla.org/) 

on the downloads page is the route i normally go down.

Kind regards

---

### Post by Yezinki on 2010-11-03
[http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/)

Which one of of these?

Regards!

---

### Post by matt_symes on 2010-11-03
Hi

I have always used the Stable (Debian-based) version.

[http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php](http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php)

Pick the one based on your requirements and hardware. I generally get the .iso and burn to CD but you can create a live USB. The docs on the clonezilla site explain.

Kind regards.

---

### Post by Yezinki on 2010-11-03
Thanks for posting the link, which I highly appreciate.

How do you rate the quality of a Full back up restore?

Best Regards!

---

### Post by Quackers on 2010-11-03
> **Yezinki said:**
> Thanks for posting the link, which I highly appreciate.

How do you rate the quality of a Full back up restore?

Best Regards!

If the backup image runs ok, and the restore image works (by testing) I consider it a valid option :-) Clonezilla has worked for me using the Live CD.

---

### Post by Yezinki on 2010-11-03
One more question whats the approx size of the image, can it be burnt on media, it's file type & approx duration of Image creation?

Can it image /restore windows/NTFS too?

Regards!

---

### Post by Quackers on 2010-11-03
Clonezilla images are compressed and they don't copy empty space so they will be smaller than your hard drive, but how small depends on what's being copied. Again, the amount of time it takes depends on how much is being copied. For me it takes about 30 minutes per hard drive, but my hard drives (250GB) are nowhere near full. I have also backed up Windows as well with Clonezilla.

---

### Post by Yezinki on 2010-11-03
Woh so you mean to say that it can create a Full back image of a machine with windows & Ubuntu & restore it.

I wont need ATI Home 2011 any more thats great, coz that doesn't support etx4 files.

Best Regards!

---

### Post by matt_symes on 2010-11-03
Hi

Clonezilla will do the lot. Read up on how to use it.

Kind regards

---

### Post by HermanAB on 2010-11-03
Howdy,

Making full images is really a Windows thing, because Windows and all its applications are very difficult and time consuming to install.  

The latest and greatest version of Linux however can be installed from scratch with all applications in about 30 minutes, which is much, much faster than restoring a full backup image.  

In 3 years or so when your HD fails, would you want to install a 3 year old delapidated version of Linux from backup, or would you want to install the latest all singing and dancing version?

Therefore, the better way of doing things is to only backup your data and forget about backing up the rest of the system.

---

### Post by HermanAB on 2010-11-03
Why why is is the the post post double double....

---

### Post by Yezinki on 2010-11-03
Thanks matt_symes & Herman AB for your replies & assistance.

Best Regards!

---

### Post by Quackers on 2010-11-03
I agree HermanAB, up to a point.
For the less Linux experienced a failed update or a blank screen on boot is more worrying. It is nice to know that if all else fails you can at least go back to your latest image.

---

### Post by Yezinki on 2010-11-03
Quakers you read my mind.

I mean after a fresh install of windows & 2 Ubuntu variants would like to take a base Full Back up image of the machine just in case.

Best Regards!

---

### Post by matt_symes on 2010-11-03
Hi

And it can be useful to do before an upgrade, in case the upgrade fails 10.04->10.10 as opposed to a fresh install of 10.10. It gives a fall back position.

Great second post hermanAB. Made me chuckle

Kind regards

---

### Post by Yezinki on 2010-11-03
Thanks matt_symes I shall give it a try.

Best Regards!

---

### Post by Yezinki on 2010-11-03
matt_symes.........my machine has an Intel Core Duo T2400 CPU........is that ok?

Best Regards!

---

### Post by matt_symes on 2010-11-03
Hi

If you are talking about the minimum spec's for ubuntu they are here.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Some hardware is problematic, but if have any problems you can always ask here.

Kind regards

---

### Post by Yezinki on 2010-11-03
Hi there,

What should ideally be the location of a full back up that could be accessed using a boot CD for restoration?

Regards!

---

