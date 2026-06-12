---
title: "Recovery after WinPP"
date: 2010-04-27
forum: General Help
---

### Post by Ebere on 2010-04-27
Edit: I got the title wrong. It is WinDD, not WinPP

I wanted to backup, (Clone), my laptop, before wiping it and installing ubuntu.

I found a simple little program called WinDD that would do it.

Well... There is nothing at all, anywhere... That warns you that the destination drive will be wiped out !

I thought it would simply be cloned into a directory, or something. Not replace everything on the destination drive.

I had a LOT of irreplaceable stuff on that drive.

Is there any way to recover from this and get my old drive back ?

---

### Post by Ebere on 2010-04-28
Sorry about the mis-title.

No ideas ???

---

### Post by FiReiSFuN on 2010-04-28
I am sorry to tell you, but all of the stuff on your destination drive has been destroyed.

The "dd" utility on unix has earned the nickname "disk destroyer" for this very reason.

You did have a backup of your data though, right?

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Not necessarily... [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by FiReiSFuN on 2010-04-28
That link could be helpful to recover deleted files, or files from a failed drive. But from what the OP has said, they have actually overwritten data in the target partition with data from another partition. Any data that was residing in the overwritten blocks will be gone.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Unless the data has been extensively wiped there are ways to get at it. Don't lose hope OP. Just do some research and see about forensic tools that may help you. You may get lucky...

---

### Post by Ebere on 2010-04-28
Thank you to both of you.

The hard drive in question is an external 500Gig.

The clone that overwrote it is less than 8 gigs.

There is a small partition at the beginning of the hd where the clone resides, and the rest is simply unallocated.

I wish there were some way to tell a program to look for old partitions, complete. 

Then restore the old partitions... wiping out the new ones.

I am running testdisk right now. 

I don't have a lot of hope that it will work, because I have already run it once. It came up with nothing but the clone.

I just decided to run it again, and tell it to assess, assuming no partition tables.

---

### Post by Ebere on 2010-04-28
And by the way... This external HD WAS my backup.

There was a lot of stuff on there that is no longer anywhere else, since I started messing around with different distros, trying to figure out which one I like best.

That external HD was the only thing I had, that had enough capacity to clone the laptop to. Otherwise, I would have used something else.

Like I said, there is absolutely nothing anywhere, in any way informing the user that the clone will completely wipe and overwrite the destination hard drive.

IMO, an unconscionable neglect.

---

### Post by Dayofswords on 2010-04-28
i would wait before you start doing anything on the disk until you know what you should do to  recover your stuff (hopefully a good amount)

---

### Post by Ebere on 2010-04-28
Ok, I tried GParted.

I tried TestDisk.

No joy.

Right now... I have PhotoRec running.

Looks like it will take a few hours, to finish.

I have no idea whether it is actually 'recovering' all the files, or just the files on the new clone.

I'll know when it is finished. 

But it IS doing something...

---

### Post by Ebere on 2010-04-28
All I did was hit the refresh button for this page, and it posted my last post, a second time.

Sorry about the extra post.

---

### Post by Ebere on 2010-04-30
Update:

The photorec program only got through a small part of the disk, and then kakked with some sort of dump error.

What it did get through, and write to the other disk...

It's all basically the same filename, with different numbers in the name.

Many files are cut into smaller chunks.

Most of what is there, is pretty much useless.

It did pick out a few pics from archives of websites I have built or managed. That's about as far as the usefulness goes, though.

I still haven't written anything else to the disk. (Unless testdisk, or photorec write something, in their process.)

So I am still hoping to find a utility that will actually recover the contents of that disk as it was. Or at least as much of it as possible.

---

