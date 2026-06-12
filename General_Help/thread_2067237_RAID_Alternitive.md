---
title: "RAID Alternitive"
date: 2012-10-06
forum: General Help
---

### Post by hcker2000 on 2012-10-06
I have been searching around for an alternative to raid now that I have had my second raid 5 failure that resulted in a total lose due to the unrecoverable read error(URE) during the rebuild process.

So I'm looking for some thing much simpler. If all else fails I'm going to just use multiple disks and manage whats on them my self.

IF I could pool them all into one drive and still be able to access all the other data if a drive fails that would be ideal.

I have also looked into flexraid but I'm not positive it does not suffer from the same unrecoverable read error issue as well.

I'm also doing bi-weekly disk to disk backups with external drives as well.

So please give me some ideas of a better solution than raid.

---

### Post by Cheesemill on 2012-10-06
What type of RAID are you using?
Software or hardware, number of disks, RAID level, etc...
I've only ever had a properly configured RAID die on me once (and that was due to a hardware controller failure).

There are other options than RAID but it would be interesting to figure out why your RAID is failing.

Other alternatives include Greyhole and ZFS:
[http://www.greyhole.net/](http://www.greyhole.net/)
[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

---

### Post by hcker2000 on 2012-10-06
Right now its software (mdadm) raid 5 comprised of four 1tb disks. Three of which have a run time of 2.7 years. One died a while back and its replacement has a run time of 120 some days.

Here are the steps as they happened.

Woke up and heard click of death and found a drive removed from the raid 5 (all data intact still)
Ran a couple benchmarks on the disk that was removed to see if it would repeat the click I heard earlier.
It did not so I added it back to the set and let it try to rebuild it.
Go to work
Wife tells me that she cant access any files.
I SSH in and see that another drive has been booted from the array and the drive that was clicking was also no rebuilding any more.

So the only thing that I can think that happened is that during the attempted rebuild on the probable bad drive I got a URE and mdadm booted the disk from the array which means there were not enough disks to continue the rebuild.

Whats very odd is that the disk that was kicked from the URE has no super block any more. The suspected bad disk still has its supper block but is marked as out of sync so I can't start the raid set.

---

### Post by dcstar on 2012-10-07
> **hcker2000 said:**
> I have been searching around for an alternative to raid now that I have had my second raid 5 failure that resulted in a total lose due to the unrecoverable read error(URE) during the rebuild process.
........
So please give me some ideas of a better solution than raid.

When a RAID 5 (or whatever) array is rebuilding there is NO redundancy until the rebuild is 100% complete, a failure in the existing working drives will cause loss of data. When a group of drives are at a certain age and one fails then the chances of another identical drive - that has done the same amount of work for the same amount of time - failing are high. Rebuilding a RAID array is an intensive process that will stress the existing drives and push any borderline units towards failure.

There are plenty of ways of using RAID to reduce the chances of losing data, the best way is to have a hot-standby drive in the array that is immediately used once a problem is detected.

All of these options are trade-offs between the cost of the redundant hardware versus the protection you get, so the more you spend the more protection you have.

---

### Post by bab1 on 2012-10-07
> **hcker2000 said:**
> I have been searching around for an alternative to raid ...

So please give me some ideas of a better solution than raid.

You might want to carefully [**[COLOR="Blue"]read this[/COLOR]**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/").

---

### Post by hcker2000 on 2012-10-07
> **bab1 said:**
> You might want to carefully [**[COLOR="Blue"]read this[/COLOR]**]("http://storagemojo.com/2012/07/23/the-post-raid-era-has-begun/").

I have read several articles stating the same thing and thats why I have felt its time to stop messing with the raid setup and just have a bunch of disks that I manage myself. I will do disk to disk copys onto external drives that can be fully powered down once the backup has run.

---

