---
title: "What is .encryptfs and why is it using so much data?"
date: 2012-01-02
forum: General Help
---

### Post by dorlow on 2012-01-02
My hard drive was full.  I was able to remove one huge file that freed up about 20 GB.  But my HD full size is 500 GB.  Right now I'm looking at "Disk Usage Analyzer."  It's showing ".encryptfs" is using up 246.2 GB and my "david" (home folder) is using up 246.2 GB.  Then the next folder to use the most disk space is user, which is using 2.7 GB, then var which is using 861 MB.  

What is .encryptfs?  I can take the hint by the name that it's something to do with encrypting my filesystem.  But it seems like a huge waste if the system needs to duplicate all my data to encrypt it.  Is there anyway to eliminate that folder?

---

### Post by Paqman on 2012-01-02
> **dorlow said:**
> It's showing ".encryptfs" is using up 246.2 GB and my "david" (home folder) is using up 246.2 GB.

The clue is that they're identical in size. Ecryptfs is your encrupted home folder. Don't worry, the actual space consumed by both ecryptfs and your home folder is 246.2GB, not 492.4GB as you might think.

---

### Post by dorlow on 2012-01-03
> **Paqman said:**
> The clue is that they're identical in size. Ecryptfs is your encrupted home folder. Don't worry, the actual space consumed by both ecryptfs and your home folder is 246.2GB, not 492.4GB as you might think.



Then I dont understand why I ran out of hard drive space.  I have a 500 gb hd.  Below my home folder in data usage was a folder using like 3 gb.  But it doesn't make sense to me either way.  With 246x2 is so close to 500 it doesn't leave room for the 3 gb and 500 mb folders.  But 246 gb + 3 gb + 500 mb isn't anywhere near 500 gb so why did my hard drive fill up?

---

### Post by MartijnNL on 2012-01-03
You say your disk is full. Was this just based on the Disk Usage Analyzer or did you actually run into problems?

Based on [this thread]("http://ubuntuforums.org/showthread.php?t=1560411") one of the two is a virtual filesystem which doesn't actually take any physical disk space. Only the Disk Usage Analyzer doesn't seem to recognize this. And some other programs also seem to have a problem with it. But your disk isn't actually full.

---

### Post by dorlow on 2012-01-03
I wasn't able to write any more files.  When opening up a terminal window and typing df it showed I had 0 free space.  That's when I opened up disk analyzer and notice it appeared my home and encryped folders were duplicating my usage.  I freed up some space.  But it still looks like I'm wasting a ton of space there.

---

### Post by Paqman on 2012-01-04
It's often handy to run Disk Usage Analyser as root, just in case you've got some big fat files owned by root that are taking up space. To run it as root:
```

gksudo baobab

```

---

