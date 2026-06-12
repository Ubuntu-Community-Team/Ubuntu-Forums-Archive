---
title: "xfsdump on devices or directories?"
date: 2009-06-25
forum: General Help
---

### Post by Copperblade on 2009-06-25
I used xfsdump for the first time today, and everything was successful, but there are a couple things I don't understand.

When I tried to dump using the directory name like:

xfsdump -f /path/to/dumpfile /directory/

it did not work.  So without unmounting it, I used the device name instead:

xfsdump -f /path/to/dumpfile /dev/device

and it worked perfectly.  So...

1) Why does the example in the man page give a directory as the argument, but it did not work for me?

2) I didn't try this with an unmounted filesystem, but I presume it will work on the device regardless if it's mounted or not.  Why does the man page say "xfsdump does not dump unmounted filesystems"?

3) Why did xfsrestore work with the directory and not the device?


Also as a side note, I tried to do an incremental dump via:

xfsdump -l 1 -f /path/to/dumpfile /dev/device

but it produced an error.  Just looking for feedback if anyone has any comments.

---

