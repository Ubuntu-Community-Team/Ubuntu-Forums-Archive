---
title: "how to delete corrupt file on NTFS partition  after dd_rescue (10.10)"
date: 2011-12-28
forum: General Help
---

### Post by LMHmedchem on 2011-12-28
Hello,

I have a hard drive with some bad sectors. This was in a windows box, so the drive has two ntfs partitions on it. I recovered the data to a new drive using ddrescue from a ubuntu live flash stick. That process seems to have gone fine, here is the summary,
```

Summary for /dev/sda -> /dev/sdc:
dd_rescue: (info): ipos: 976762560.0k, opos: 976762560.0k, xferd: 976762560.0k
                   errs:     24, errxfer:        12.0k, succxfer: 976762560.0k
             +curr.rate:     3064kB/s, avg.rate:    37374kB/s, avg.load: 10.9%

```
You can see there there were some errors.

I am now using cp -Rfp to copy the data from the new drive where the dd data was sent and put it on an external backup drive. I have some errors from cp so far.

cp: cannot access `data/applications/sm2_profiles/yahoo/newstf/Cache.Trash/Trash/Cache': Input/output error 

I presume this is a file that dd_rescue could not get all of and is unreadable. Is there any way in ubuntu that I can delete this corrupt file. I would like to do this before putting the drive back into the windows box.

I can post the entire log from dd_rescue if that would be useful.

LMHmedchem

---

### Post by LMHmedchem on 2011-12-28
Since making this post, I have been informed that the I/O error indicates a corrupt *[COLOR="Red"]file system[/COLOR]*, not a corrupt file. This means I need to repair the file system as opposed to deleting the file. Since this is a drive with two ntfs partitions, I am wondering if I can use fsck and if there are any special arguments to let it know that this is an ntfs partition.

I could also put this back into a windows box and let chkdsk run, but since I am already in ubuntu, it seems to make sense to try a linux tool. I generally have more confidence in linux tools anyway.

LMHmedchem

---

