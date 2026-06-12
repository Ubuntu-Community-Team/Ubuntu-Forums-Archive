---
title: "RAID-1 of /boot not working"
date: 2011-09-04
forum: General Help
---

### Post by Kissell on 2011-09-04
I have been a user of software RAID in Linux for a long time, there are some nice advantages over hardware.  Anyway, I normally just use RAID for my data, but decided for the first time to try to software RAID mirror my OS so that I would have less points of failures on my main server.

I used the standard Ubuntu 11.04 GUI installation and created a "/boot", "/", "/home", and "swap" partitions on two separate disks and used the installation GUI to mirror them.  Everything seemed to run okay.  

Then I decided to pull one of the hard disks to test it.  Got the following error (returned from Ubuntu):
> "The disk drive for /boot is not ready yet or not present" during boot.

---

