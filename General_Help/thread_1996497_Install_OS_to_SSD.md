---
title: "Install O/S to SSD?"
date: 2012-06-04
forum: General Help
---

### Post by Dan Again on 2012-06-04
I am thinking about building a relatively simple desktop computer. I just got an ultrabook and love the super quick start times. If I get a small SSD and install my O/S on that and then use a larger traditional HDD for file storage, will I see similar benefits? Is a 30G SSD sufficient for these purposes? Any tips on doing something like this?

---

### Post by pqwoerituytrueiwoq on 2012-06-04
30gb is plenty
even a 16GB will do
if you are going to have a sata 3 mobo you way want this one since a fast 30gb sata 2 is only 5$ less
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227728](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227728)

i would suggest you put /var, /home, /root on a normal HDD and /tmp on ram for the best possible life span on the ssd don't forget noatime and discard in fstab
i am using this one
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820233266](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233266)
i had one scare a few days (6 power on days) in when the system became read-only every time i tried to install a update
i unplugged it and plunged it back in and copied everything to a hdd and updated on the hdd, decided to try the ssd again and i installed the updates and it worked this time

---

### Post by oldfred on 2012-06-04
I got a 60GB SSD and set two 25GB root partitions where all my data is on the rotating drive. Second 25GB is now 12.10 for testing.

I prefer to have an entire system on one drive including MBR & /home (but no data in /home so it is tiny) and any essential partitions required to boot. And an install on every drive including rotating drive(s). Then if a drive fails I can boot the other even if I get errors on swap, or data partitions not mounting from failed drive.

---

### Post by blind2314 on 2012-06-04
> **pqwoerituytrueiwoq said:**
> 30gb is plenty
even a 16GB will do
if you are going to have a sata 3 mobo you way want this one since a fast 30gb sata 2 is only 5$ less
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227728](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227728)

i would suggest you put /var, /home, /root on a normal HDD and /tmp on ram for the best possible life span on the ssd don't forget noatime and discard in fstab
i am using this one
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820233266](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233266)
i had one scare a few days (6 power on days) in when the system became read-only every time i tried to install a update
i unplugged it and plunged it back in and copied everything to a hdd and updated on the hdd, decided to try the ssd again and i installed the updates and it worked this time

The scares and worrying about SSDs wearing out quickly with multiple writes don't really apply anymore...feel free to put the filesystems where you wish, but it won't "damage" your SSD to leave them there as well.

---

### Post by buzzingrobot on 2012-06-04
I boot off an SSD and it's great.  Fast  and quiet.  

I'd suggest opting for manual partitioning when you install.  Put "/" (root) on the SSD. Put /home, /usr, /usr/local, /tmp, /opt, /var, /srv on another drive(s).  Those partitions are listed as suggested options when you  select manual partitioning during an install.  If you don't set them up in their own partitions, they will default to being created under / on the SSD.  /tmp and /var, especially, can eventually take up a fair amount of space.  With 30 gigs, play safe and move them off the SSD.

Read up on adding options intended to keep the SSD happy.  I have a NewEgg SSD, as well, of a different brand.  NewEgg says no special options are needed to optimize it, so I don't use any.

In any case, /etc/fstab is the file that maps out your partitioning scheme.  It's read at boot by the system.  You add options by editing this file. Here's the thing:  If you make a mistake editing /etc/fstab, your system may not boot or it may boot with the drives in read-only mode.  The latter means that even if you edit /etc/fstab to correct the errors, you can't save the file. Obviously, be very careful editing /etc/fstab.  Make a copy of the file before you change it. And don't change it unless you are certain you need to.

(I would not add options to /etc/fstab just to see if performance increases.  Go the option route only if you have specific problems you want to correct. Much of the guidance about SSD's on the web comes from the technology's early days and may or may not be applicable today.)

---

### Post by Dan Again on 2012-06-04
Thanks for all the great info, guys. Based on my needs and the current costs of SSD's, though, I'm starting to think I might just opt for relatively large SSD for O/S and files. We'll see...

---

### Post by inashdeen on 2012-06-04
All the best. agree with what said above. scare about SSD is much less now. simply install your ubuntu on that SSD and later mount that HDD on your system. otherwise, set your HDD as /home

---

