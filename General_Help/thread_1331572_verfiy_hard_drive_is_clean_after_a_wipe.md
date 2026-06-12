---
title: "verfiy hard drive is clean after a wipe"
date: 2009-11-19
forum: General Help
---

### Post by lmm5247 on 2009-11-19
i'm selling my old hard drive on ebay and i wanted to wipe it clean before selling. i used dban to write 1's and 0's over everything. then used 

```
sudo dd if=/dev/zero of=/dev/sdb
```

then used

```
sudo shred /dev/sdb -f -v -z --iterations=6
```

i'm paranoid, i know lol. but anyway. i was just wondering if there is a tool i can use to verify that its wiped.

thanks  =)

---

### Post by scragar on 2009-11-19
Shred alone in that case is overkil.
1 itteration of random should have been good enough for most hard drives(and since most users are idiots at recovering data 99% of the time that's overkil), and for a hard drive that's very new then 1 itteration and zeroing it out is more than enough.

If you want to do this in future unmount the drive, then run:```
sudo shred /dev/sdb -vz -i 1
```

---

### Post by bodhi.zazen on 2009-11-19
You need but write all zeros once with dd.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

---

### Post by Commander_Keen on 2009-11-19
I would run the Ubuntu CD live.
and have it format the Hard drive 14 times.

---

### Post by Mike'sHardLinux on 2009-11-19
> **Commander_Keen said:**
> I would run the Ubuntu CD live.
and have it format the Hard drive 14 times.

:shock:

---

### Post by bodhi.zazen on 2009-11-19
> **Commander_Keen said:**
> I would run the Ubuntu CD live.
and have it format the Hard drive 14 times.

That is completely unnecessary, see the link I gave in my first post.

In addition , formatting a drive does not over write the data. You need to write zeors (or 1's) to the drive.

---

### Post by Mike'sHardLinux on 2009-11-19
I sincerely hope Commander_Keen was kidding. 

By the way, great link, bodhi.zazen.

---

### Post by philinux on 2009-11-19
> **bodhi.zazen said:**
> You need but write all zeros once with dd.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

Nice.

---

### Post by oldsoundguy on 2009-11-19
Passing this on.
I have used (and still use) a floppy disk program (free) called Killdisk.  It makes ONE pass as that is sufficient for 99% of the average bears removals.  Government work requires more passes.  And unless your drive falls into the hands of someone with some serious forensics software, your tush should be covered.

BUT .. ULTRA IMPORTANT ... make sure the disk is ALL ONE PARTITION .. use Gparted to re-connect all partitions.

I have purchased hard drives that have been partitioned and the primary C partition was wiped clean.  HOWEVER the added partitions were NOT and were loaded with sensitive data!

---

### Post by Mike'sHardLinux on 2009-11-19
Or you could simply wipe all partitions...but I guess that would be a little more work.

---

### Post by lmm5247 on 2009-11-20
> **oldsoundguy said:**
> Passing this on.
I have used (and still use) a floppy disk program (free) called Killdisk.  It makes ONE pass as that is sufficient for 99% of the average bears removals.  Government work requires more passes.  And unless your drive falls into the hands of someone with some serious forensics software, your tush should be covered.

BUT .. ULTRA IMPORTANT ... make sure the disk is ALL ONE PARTITION .. use Gparted to re-connect all partitions.

I have purchased hard drives that have been partitioned and the primary C partition was wiped clean.  HOWEVER the added partitions were NOT and were loaded with sensitive data!

in addition to all the stuff i used, i used the killdisk program too in windows.

but lemme ask a stupid question. my hard drive has 4 partitions on it, are they all wiped clean? wouldn't shred wipe EVERYTHING?

---

### Post by louieb on 2009-11-20
You could alway run **testdisk** and see if it can find/recover anything. [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") its in the repositories

---

### Post by stonebit on 2009-11-20
I've used shred and find it a bit slow, but it's the best option if you don't have a spare machine or must keep yours up. 

I would go with DBAN - [http://www.dban.org/](http://www.dban.org/) . DBAN wipes any drive to your desired security concern. It is also very fast as far as wiping goes. Just make sure you don't wipe the wrong drive if you have multiples in a system. After DBAN, no file recovery is remotely possible. 

Please don't think formating a disk wipes it. That's the worst advice i've heard in a long time. Formating just changes the file pointers so the OS ignores that bock on the hard drive, but all the data remains.

---

