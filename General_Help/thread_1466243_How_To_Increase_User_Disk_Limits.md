---
title: "How To Increase User Disk Limits?"
date: 2010-04-30
forum: General Help
---

### Post by KernelKing on 2010-04-30
I'm running Ubuntu 9.10 LTS.

Total filesystem capacity: 15.4 GB
used: 10.1 GB
available: 5.2 GB

/home = 2.8 GB
/home/jack = 2.8 GB ~ 100.0% of /home

question?

How do I increase the disk capacity for /home/jack?

I looked into quota and related utilities and there doesn't seem to be any quotas in place, at least looking at /etc/fstab.  I'm puzzled.

TIA for any help.

---

### Post by mikewhatever on 2010-04-30
Do you have a separate home partition?

df -h

---

### Post by KernelKing on 2010-04-30
No, it doesn't seem that I do:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G   11G  4.3G  71% /
udev                  2.9G  232K  2.9G   1% /dev
none                  2.9G  404K  2.9G   1% /dev/shm
none                  2.9G  120K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw


> **mikewhatever said:**
> Do you have a separate home partition?

df -h

---

### Post by dcstar on 2010-04-30
> **KernelKing said:**
> No, it doesn't seem that I do:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              16G   11G  4.3G  71% /
udev                  2.9G  232K  2.9G   1% /dev
none                  2.9G  404K  2.9G   1% /dev/shm
none                  2.9G  120K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw

```
mount | grep sda1
```

---

### Post by mikewhatever on 2010-04-30
Do you have an OEM install of some kind? Which OS? 9.10 and LTS are two separate releases. Which one do you have?

---

### Post by KernelKing on 2010-04-30
> **dcstar said:**
> ```
mount | grep sda1
```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

---

### Post by KernelKing on 2010-04-30
> **mikewhatever said:**
> Do you have an OEM install of some kind? Which OS? 9.10 and LTS are two separate releases. Which one do you have?

I probably shouldn't have said LTS...

lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

---

### Post by dcstar on 2010-05-01
> **KernelKing said:**
> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

So it's ext3 then, that just clears up any doubt.

Now, the question is why you think that your /home is full?

---

### Post by KernelKing on 2010-05-01
> **dcstar said:**
> So it's ext3 then, that just clears up any doubt.

Now, the question is why you think that your /home is full?

(These numbers come from the graphical Disk Usage Analyzer.)
/home = 2.8 GB
/home/jack = 2.8 GB ~ 100.0% of /home

I'm down to my last ~100 mb in /home/jack.  When I create files, I get warning that I am out of space and the script terminates.  I delete files to make room.  How do I increase the allocation of /home/jack (or /home) to say 4GB?

---

### Post by KernelKing on 2010-05-01
> **KernelKing said:**
> (These numbers come from the graphical Disk Usage Analyzer.)
/home = 2.8 GB
/home/jack = 2.8 GB ~ 100.0% of /home

I'm down to my last ~100 mb in /home/jack.  When I create files, I get warning that I am out of space and the script terminates.  I delete files to make room.  How do I increase the allocation of /home/jack (or /home) to say 4GB?

No answers despite all the questions.  I'll try increasing the total disk space for this virtual image (VMWare) and see what happens.

---

### Post by KernelKing on 2010-05-01
> **KernelKing said:**
> No answers despite all the questions.  I'll try increasing the total disk space for this virtual image (VMWare) and see what happens.

I expanded the parent partition by 4GB and /home/jack still shows near 100% usage of /home.  Nothing has changed.

Help?

---

### Post by krismatth3 on 2010-05-01
It seems to me that you are confused.  Graphical disk analyzer is telling you the full size of home. it's also telling you one user is using all that space. it is NOT telling you you're out of space. I think you're misinterpreting the output of that tool.

---

### Post by KernelKing on 2010-05-01
> **krismatth3 said:**
> It seems to me that you are confused.  Graphical disk analyzer is telling you the full size of home. it's also telling you one user is using all that space. it is NOT telling you you're out of space. I think you're misinterpreting the output of that tool.

Thanks for the reply.  Let's say that I am misunderstanding the output of disk usage analyzer.

Let's move on to a deeper understanding of the situation.

Is it reasonable for a filesystem that reports ~5GB free to have the one sole user see warnings from the OS about lack of storage space?  What would cause that?

---

### Post by KernelKing on 2010-05-02
So basically after all the questions, all you guys could tell me is that I don't know how to interpret Disk Usage Analyzer.  You guys are geniuses.

---

