---
title: "HELP!  Can't mount filesystem - short read error.  Need some advice on next steps"
date: 2010-10-20
forum: General Help
---

### Post by jimmy the saint on 2010-10-20
Hey all,

So I awoke this morning to an unbootable system which cannot mount /dev/sda6 (/) and "short read" errors.  I am attaching an image of my screen to provide more detail w/o having to type out all the messages.  

Anyway, I will attempt to run fsck as soon as my /home is properly backed up (my last backup is 3 weeks old as I've been away from home).  I have a few questions, as I have never had this sort of issue before.

1) I am told by the machine to run fsck manually.  Does that mean to simply run ```
fsck /dev/sda6
``` or do I need a few options in there?

2) How can I then test the health of my drive?  I would hate to go through the drama of fixing these filesystem errors, only to have it crap out on me again next week.  Fortunately (I suppose) I am sick as hell today and took the day off anyway.  I usually don't have the luxury of days off.

3) I am considering taking advantage of this situation to upgrade to 10.10 from 9.10 by way of a fresh installation, which is why I would like to check the health of the disk first.  When I move the contents of /home to the new /home created in the 10.10 install, should I simply ```
chown -R user:group /home/user
``` or is there a better way to handle that?

4) Any general tips regarding this type of issue would be appreciated.  

Thanks all,

JTS

---

### Post by jimmy the saint on 2010-10-21
bumpitty bump bump

---

