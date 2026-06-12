---
title: "Is Ext4 ready?"
date: 2010-05-14
forum: General Help
---

### Post by piratebill on 2010-05-14
I am about to upgrade all my systems this week.  I have been holding off on Ext4 because last I heard there were bugs with rather large files (over 50 gig or something like that) getting corrupted.  Is Ext4 mature enough now to trust my data on?  Have any of you had issues with it?

---

### Post by The Cog on 2010-05-14
I have installed seven systems on ext4. Four of those were Jaunty, three were Karmic. All seven ended in fatal filesystem corruption causing inability to boot, after a lifetime between 3 hours and 3 months. I will not trust ext4 again.

That said, I haven't seen anyone else reporting that kind of wholesale corruption, which seems odd.

---

### Post by blueridgedog on 2010-05-14
I have taken the plunge, but have also seen several posts that suggest there are issues.  I have a solid backup plan onto rotating hot swap drives that run ext3, so I feel covered.

---

### Post by bigsmitty64 on 2010-05-14
Both Karmic and Lucid here, with no problems.

---

### Post by Sin@Sin-Sacrifice on 2010-05-14
Since jaunty with no problems.

---

### Post by Ron S on 2010-05-14
Ive had it on my P.C. and laptop since jaunty with no problems. I think the biggest problems occur if you do a hard shutdown. At UDS they proposed  btrfs to be the file system to replace Ext4 in maverick so you may want to wait till then to see what happens.

---

### Post by darolu on 2010-05-14
I think EXT4 is mature neough, those bugs were solve time ago, if you have ext2 or ext3 fs working it should be easy to upgrade to ext4.

If you are running a server and are looking for the most stable filesystem, I'd recommend XFS though.

BTRFS is NOT ready yet, it is in active development right now, so I wouldn't recommend using it, at least not yet; I doubt it will replace Ext4 as the default filesystem in Ubuntu in 10.10 as it is not stable enough.

---

### Post by slibuntu on 2010-05-14
4 server installs, 6 laptop installs, all ext4, no problems so far.

There were a few bugs near the beginning, but they appear to be a thing of the past. I'd recommend it, it's much quicker that ext3.

---

### Post by foxmulder881 on 2010-05-14
As darolu mentioned, for file sizes of that sort you should be running XFS.

Generally speaking though, ext4 is just as stable as ext3 is. If not better. It's definitely faster. Personally, I'm running ReiserFS! :P

---

### Post by slibuntu on 2010-05-14
> **foxmulder881 said:**
> As darolu mentioned, for file sizes of that sort you should be running XFS.

Generally speaking though, ext4 is just as stable as ext3 is. If not better. It's definitely faster. Personally, I'm running ReiserFS! :P

Wait till you get some of the Reiser4 goodness...

[http://www.phoronix.com/scan.php?page=article&item=reiser4_benchmarks&num=3](http://www.phoronix.com/scan.php?page=article&item=reiser4_benchmarks&num=3)

---

### Post by foxmulder881 on 2010-05-15
Those benchmarks seem promising. Although it's still too early to jump in just yet. There are seemingly some good times ahead for file systems though, with the development of Reiser4, BtrFS and the uncertain future of Solaris' ZFS. It's all pretty exciting stuff happening. Let's hope Oracle decide to open source ZFS, I highly doubt it though!

---

### Post by slibuntu on 2010-05-15
Yeah, BtrFS looks like it'll be cool. I'd be surprised if we see it in Maverick though, I don't think it'll be stable enough by then. It may be an option, but it likely won't be the default, the same way that ext4 was an option but ext3 was the default a couple of releases back.

---

### Post by philinux on 2010-05-15
Been using ext4 since karmic with no problems at all. Desktop and laptop 64 and 32 bit respectively.

Very fast fsck.

---

### Post by cascade9 on 2010-05-15
I've used it a bit, here and there, noramlly for /. No problems here yet. 

> **The Cog said:**
> I have installed seven systems on ext4. Four of those were Jaunty, three were Karmic. All seven ended in fatal filesystem corruption causing inability to boot, after a lifetime between 3 hours and 3 months. I will not trust ext4 again.

That said, I haven't seen anyone else reporting that kind of wholesale corruption, which seems odd.

Gah! :( Condolences 

> **slibuntu said:**
> Wait till you get some of the Reiser4 goodness...

[http://www.phoronix.com/scan.php?page=article&item=reiser4_benchmarks&num=3](http://www.phoronix.com/scan.php?page=article&item=reiser4_benchmarks&num=3)

Nice. I still think that Btrfs is going to be the next big file system though.

---

### Post by davidogg on 2010-08-12
> **cascade9 said:**
> I've used it a bit, here and there, noramlly for /. No problems here yet. 



Gah! :( Condolences 



Nice. I still think that Btrfs is going to be the next big file system though.

Probably.

Chris Mason (of BTRFS) is also the man who added journaling to Reiserfs.

---

