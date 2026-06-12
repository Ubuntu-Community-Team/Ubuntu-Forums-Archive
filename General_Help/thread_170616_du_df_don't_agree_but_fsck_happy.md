---
title: "du df don't agree but fsck happy"
date: 2006-05-04
forum: General Help
---

### Post by bryanl on 2006-05-04
I have a breezy server install on a 10 GB partition that du -x says takes about 500 MB. However, df says I am using 9.8 GB out of 9.9 GB. I ran fsck from a live CD (dapper flight 6) and it says there is nothing wrong with the partition.

I'v also looked at nodes and am nowhere near using that allotment.

I did have a drive, known as /media/hde3 that had file i/o errors (I think the drive is bad but I wish it would just die rather than occasionally making a mess of things. It has had intermittant problems on two controllers so I am fairly sure it is a drive problem). I was using this drive as an rsnapshot backup when it decided to throw this week's tantrum. I used fsck to clear the errors on it and now its doing just fine again, thank you (for a while?) This was just prior to loosing all my root partition free space.

But that shouldn't allocate a phantom 9.3 GB on the root partition, should it? What is hanging on to all that drive space? How do I find it? How do I release it? since du doesn't see it, it must not be a file on the system. fsck doesn't see any nodes or whatever out of joint to fix. A reboot doesn't help so it must be allocated for something. What? 

How do I understand what is going on and how do I fix? At least a server re-install isn't too bad but it is a nuisance and I'd really like to understand what is going on. It shakes my confidence in ext3 file systems and the whole 'everything is a file' idea - if its a file, why doesn't it show up so I can do something with it? So I must be missing something. Any ideas about what?

---

### Post by nanotube on 2006-05-04
any interesting output for
```
sudo e2fsck -v /dev/whateveryourdeviceis
```
?

---

### Post by bryanl on 2006-05-05
e2fsck -v says clean 37769/1205312 files; 2308929/2409742 blocks
du says 463168 used
df says 9487640 / 9084388

I do notice I have now freed up another .3 GB or so. Its a puzzle.

---

