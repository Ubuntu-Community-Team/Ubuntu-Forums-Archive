---
title: "FSCK 125 Hours?"
date: 2010-05-06
forum: General Help
---

### Post by michio on 2010-05-06
Ok so I made a pretty dumb mistake while I was attempting to extend the size of my 4 disk raid by replacing the disks one at a time. I stupidly removed two and well I am sure you know what happens.

So I attempted to recreate the raid with the original disks but it was unable to mount. At this point I ran foremost to try to pull of some files which was moderately successful.

I then started an FSCK -y. It has since been running for well over 5 days. It has been displaying the below message since about the first hour or so on different files.
```
Clone multiply-claimed blocks?
```

The raid is 1.5 terabytes across 4 disks
I have a few of questions; 
1) is there anyway to check how far along the fsck is (aprox how much longer it may run for?
2) Is this an a appropriate amount of time for this to take?
3) Is there a chance of this working (i.e getting this disk mountable) or is it just a waste of time?

As you can tell I am no expert with this so please be patience with me.

---

### Post by michio on 2010-05-07
Now its pushing 150 hours.
Any insights?

---

