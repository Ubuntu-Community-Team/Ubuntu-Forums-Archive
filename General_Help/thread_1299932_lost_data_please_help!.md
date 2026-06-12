---
title: "lost data please help!"
date: 2009-10-24
forum: General Help
---

### Post by dizzlecorn on 2009-10-24
Ok so I was trying to copy data from my laptop to my gf's external because earlier I had an issue with Jaunty and too many firefox versions.  Long story short I think I accidentally deleted the repository keys and I couldn't fix it with the live cd.  Anyway so I was trying to copy so I could start all over and I read online somewhere, maybe here what command to run after mounting both drives.  So I ran sudo cp /dev/sda1 /dev/sb1 because it wouldn't let me designate a specific folder I created.  I thought it would dump the files in any free space on the external especially because it is a 500gb external and only 70gb or so I was trying to copy.  I read other posts and download testdisk/photorec did a dry run as I don't have another external big enough with me right now. 
My question is will this even work?  The small amount of files that it did find didn't look familiar so maybe it is working but then again I saw a handful that are from the bunch I was copying from my laptop.  Right now windows sees the external but won't open it because it was NTFS but after the copy it's now in ext3 format.  Somebody please help!  I might as well be dead F my life!

---

### Post by dizzlecorn on 2009-10-24
Forgot to mention that I also have getdataback anybody know which would yield the best results?

---

### Post by mr_steve on 2009-10-24
I hate to say it, but I think you're pretty well hosed. The command you entered will have copied your entire sda1 partition onto sdb1, starting at the beginning. Thus, however big the sda1 partition was, you will have overwritten that much of sdb1. Some data recovery tools may be able to get back files from the rest of the drive, but that first chunk is probably well and truly gone.

---

### Post by dizzlecorn on 2009-10-24
Thanks for the reply.  I heard of others installing an OS over their drive and still be able to recover data with photorec.  Is my situation different?

---

### Post by mr_steve on 2009-10-24
How big was the partition that you were copying from? Did you let it run until it finished, or did you realise something was wrong and interrupt it? Basically what that command did was copy the raw filesystem from your drive onto the external drive, starting at the beginning. So if you had say a 20GB partition you were copying from, the first 20GB worth of files will have likely been completely overwritten, but testdisk or photorec may be able to recover the files from beyond that point.

---

### Post by dizzlecorn on 2009-10-24
I think that's the problem.  I'm almost positive that there was less information on the drive than what I copied to it.  I let it finish because I couldn't see what was going on from the terminal or nautilus.

---

