---
title: "restore a file after a   &gt;file1"
date: 2010-06-30
forum: General Help
---

### Post by issamneo on 2010-06-30
good Morning guys;
a collegue has done this for a shell script > test1.sh .lol
now i must rewrite the script.
do you have any idea to find my script?
thanks.

---

### Post by bokopperud on 2010-06-30
I don't think it's possible.

Usually when you overwrite a file (cp, mv, ...) a new inode is used, and the old is just added to a list over free inodes.  I assume also the areas on the disk used by the retired inode, will be added to the list over free space.  Such a file can be recovered until the inode and/or space is reused.

However when you use redirecting (>), you actually use the existing inode.  I'm not quite sure if you also be using the physical space (which sure would make recovery impossible).  It's possible that the space won't be reused, but put onto the free-list... but as you don't have the inode to tell you which parts of the list that actually was, you can't pinpoint which areas to recover.

You could perhaps use grep and do a raw search of the physical partition (i.e. grep -20 "something" /dev/sda1), but then you need to remember a specific string from your script, preferebly not found elsewhere.

---

### Post by iponeverything on 2010-06-30
I agree with @bokopperud -- the new data will have been written to the same physical location as as original data, and so nuked it in the process. If the new data was less than the original data, a remnant may still exist on the device. IMO, unless rewriting the script is really big deal, recovery is not really practical for the whatever data is still there.

---

