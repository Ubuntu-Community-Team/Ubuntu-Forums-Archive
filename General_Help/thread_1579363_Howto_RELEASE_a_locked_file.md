---
title: "Howto RELEASE a locked file?"
date: 2010-09-21
forum: General Help
---

### Post by held7over on 2010-09-21
Ubuntu 10.04

I transferred a Word Processor document via SSH2 from kristin's laptop to my desktop computer on my network the other day. Since that time, both computers have been shutdown. 

Today, I wanted to open the document and got the following notice--

> Document file 'Sound Fix.odt' is locked for editing by:
kristin ( 15.09.2010 16:08 )
Open document Read Only or open a copy of the document for editing.

All I can figure is, maybe I didn't exit the gFTP application properly. How do I release this lock on this file on my computer?

Thanks! :)

---

### Post by robsoles on 2010-09-22
Look for a .hidden file in the directory with the file that is giving you this problem (press [CTRL]-[H] if viewing using nautilus or type 'ls -al' if viewing via terminal).

If you find a .hidden file in the directory with loosely matching filename to the one you are trying to open then move the .hidden file to a different folder and try opening the file in question again.

Does it offer to open a read-only copy of the file? Do you find the .hidden file?

---

### Post by held7over on 2010-09-22
Thanks for responding robsoles.  I am sorry, I seemed to have released the lock......I was moving some files last night, which included this locked one, and that evidently released the lock....as you are suggesting it will. I will have to wait till it happens again to verify what I am doing to end up with this condition.... 

When re-looking at the file through the application gFTP yesterday which I used to ssh2 transfer it, the file listing looked something like this if I am remembering it correctly:

.~lock.Sound_Fix.odt
Sound_Fix.odt

After I had accomplished the transfer using gFTP, I just exited the program as that is how I used to use it, but it evidently didn't release the lock like it used to do...

---

