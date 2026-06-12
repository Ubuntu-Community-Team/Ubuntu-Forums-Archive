---
title: "owner mess"
date: 2010-07-03
forum: General Help
---

### Post by S.G. on 2010-07-03
I accidentally changed etc folder ownership, and now my computer doesn't even start up.

I tried starting up in failsafe mode and changing the ownership from the root console, but somehow I wasn't allowed to do that.

Then I loaded kubuntu from a live disk and I changed etc ownership to root. I thought that would clear up the mess, but apparently live disk's root is not equivalent to system's: when I try to start up the computer I get a message saying the filesystem is readonly.

I'm not too concerned, because I have a complete backup, but I'd rather avoid the time of re-installing all my software again...

Any hints?

Thanks in advance...

---

### Post by lsutiger on 2010-07-03
have you tried sudo su to become root in failsafe and then chown to root?

Also what do you get for /etc when you ls -A ?

---

### Post by freundfire on 2010-07-03
I am not the one to help here in this case, but I hope anyone comes and help you..

---

### Post by S.G. on 2010-07-03
> **lsutiger said:**
> have you tried sudo su to become root in failsafe and then chown to root?

When I restart in failsafe I get a series of options. One of them is root console. When I start the root console I am root. Somehow that didn't work. Apparently I was changing the folder's ownership, but in fact I did nothing.

Is there any way to set ownership to the correct root from the live disk? At least I get to change things from here.

Thanks...

---

### Post by S.G. on 2010-07-03
> **freundfire said:**
> I am not the one to help here in this case, but I hope anyone comes and help you..

;) My own fault, anyway. I'll be more careful from now on.

---

### Post by -humanaut- on 2010-07-03
You should be able to use the LiveCD to change permissions just make sure you mount the partition in question and Chmod it make from a terminal.

---

### Post by S.G. on 2010-07-03
> **-humanaut- said:**
> You should be able to use the LiveCD to change permissions just make sure you mount the partition in question and Chmod it make from a terminal.

I have changed the permissions. From 1000:1000 to root:root. The problem is that the live disk's root doesn't work for my filesystem. Now my filesystem is readonly, so I can't do anything from the root console I can launch from failsafe mode.

Now I'm going to try to restore ownership to 1000:1000 from the live disk and re-try to change ownership to filesystem's root from the failsafe mode.

Any hint will be greatly appreciated (I'm almost positive this won't work, but I don't want to spend the rest of my life wondering :P).

Thanks for the suggestion!

---

### Post by efflandt on 2010-07-03
Make sure that you are trying to change ownership of **etc** on the hard drive and NOT **/etc**, which would be the system you booted from (liveCD).  In other words, pay attention to path or prefix, so it does not start with "/" unless it is the full path to the mounted drive (and that drive is mounted read/write).

---

### Post by S.G. on 2010-07-03
> **efflandt said:**
> Make sure that you are trying to change ownership of **etc** on the hard drive and NOT **/etc**, which would be the system you booted from (liveCD).  In other words, pay attention to path or prefix, so it does not start with "/" unless it is the full path to the mounted drive (and that drive is mounted read/write).

Thanks. I finally gave up and reinstalled. I'm sure I did change ownership of hard disk's etc, because next time I restarted the filesystem was readonly. Also I checked it from dolphin, from the live disk, showing folder properties.

I still would like to know the way to solve this, if there is one, so if anyone knows what I did wrong and what I should have done had I not lost patience and reinstalled I'd be grateful for the info.

Thanks a lot to everybody.

---

