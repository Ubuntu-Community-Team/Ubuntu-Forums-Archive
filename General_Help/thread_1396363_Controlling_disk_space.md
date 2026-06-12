---
title: "Controlling disk space"
date: 2010-02-02
forum: General Help
---

### Post by degarb on 2010-02-02
I am unsure of why snaptic doesnt tell you how much disk space an application uses.  More cpu and ram specs and hd specs are needed in the packages.

Now, I was dupped.  I installed chrome, like it well. Faster than firefox. However, there is no way of setting disk cache limit. Or so it appears. This is a notebook with 6 gig hard drive. 

So, do I simply go snaptic package manager and uninstall it, or is there other garbage that needs removing?

Also, there is an awesome windows program called spacemonger.  I suppose nothing in linux like it.

---

### Post by zeroseven0183 on 2010-02-02
You can find at least 3 disk usage utility in Ubuntu Software Center when you type "disk space". One of them, ** Graphical Disk Map**, uses treemapping similar to what Spacemonger does.

There's a possible solution mentioned in [Chromium Issue 21677]("http://code.google.com/p/chromium/issues/detail?id=21677") that will set the disk cache size. See if that's what you're looking for.

---

### Post by degarb on 2010-02-05
I just uninstalled google chrome and lost .6 gig doing that!!   Why would I loose space removing a program?

Also, how do you do a scan disk in linux?

Also, what is simplest, fastest way to see disk usage?  graphical user interface doesn't show free space.

---

### Post by audiomick on 2010-02-05
> **degarb said:**
> I just uninstalled google chrome and lost .6 gig doing that!!   Why would I loose space removing a program?might be a log file, although that seems like a lot.

> Also, how do you do a scan disk in linux?
look at
```
man fsck
```see if that is what you want.

> Also, what is simplest, fastest way to see disk usage?  graphical user interface doesn't show free space.
look at
```
man df
```

---

### Post by degarb on 2010-02-08
> **audiomick said:**
> 


look at
```
man fsck
```see if that is what you want.


look at
```
man df
```


I take it man means manual.    fsck says it cannot be run when system mounted.  Moreover, the fact that linux doesn't use c: d: e: etc.  I would have no idea how to call any operation on the main partition, since I don't know what dev/sda1 means, assume might be first partition.  I prefer c: , much easier to remember.  Also, I won't have 26 partitions any time soon, but if I had more, I would assume aa: bb: cc: might kick in. 

And what does df stand for?  "Disk file" doesn't seem to cut it as a mnemonic for me.
 dfu or dfr would make more sense, so got to mean something else.

---

### Post by degarb on 2010-02-08
does fsck run on every boot?  or can this be called from the gui on next boot, as in windows?

---

