---
title: "Server Backup"
date: 2006-02-22
forum: General Help
---

### Post by SleightfulMind on 2006-02-22
I am looking for a method for making an image of my new server. Stupidly I configured the volumes with LVM, so now my usual backup program (acronis) only identifies the /boot and an LVM partition. The problem is that the LVM partition has to be backed up byte for byte (since acronis does not recognize its type). This is a bit of a problem since the drive is more than 60 gigs. Not only would it take too long to backup/restore, but I don't have a convenient method to store the image file (and backing it up to 2,000 CDRs is not an option).

So, is there a way to make an image of this hard drive? I know there must be a way to back up less than 800MB of data without making a 60GB image file.

My biggest concern is that the hard drive could fail and I would have to re-install the entire system. I mean its easy enough to just back up the important data files (like the sql databases, etc.), but I would really like to avoid having to re-install the whole system in the event of a crash.

Thanks for any help!

---

