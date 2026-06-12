---
title: "Deleted file while in use, space still used, still running, lost?"
date: 2011-11-02
forum: General Help
---

### Post by diversecg on 2011-11-02
There was a foolish mistake of a rm -rf on a folder that had files currently in use, the space is still allocated/used, and the application is still running (which is all amazing in itself).  Where is the file?  is it possible to retrieve/restore this file somehow?  how is this even possible?

any help appreciated

---

### Post by dcstar on 2011-11-03
> **diversecg said:**
> There was a foolish mistake of a rm -rf on a folder that had files currently in use, the space is still allocated/used, and the application is still running (which is all amazing in itself).  Where is the file?  is it possible to retrieve/restore this file somehow?  how is this even possible?

any help appreciated

The "file" is probably in memory, once you shut down it will be gone.

You should not use the command line for things like that, a GUI moves things to trash so you can recover.

---

### Post by HermanAB on 2011-11-03
Howdy,

The file is still there, but since it is in use, the file system marked it for deletion and it will be deleted as soon as you exit the program and the file is no longer in use.

So, how to unmark it?  Very good question...

---

### Post by crdlb on 2011-11-03
It should be possible as long as the process is still running: [http://www.linuxplanet.com/linuxplanet/tips/6767/1](http://www.linuxplanet.com/linuxplanet/tips/6767/1)

---

### Post by diversecg on 2011-11-03
Going to crdlb suggestion, will post results.

So good news is I am able to copy the file, in process of copying 200G  :)

Hope all finishes..  

  Thanks!

---

### Post by diversecg on 2011-11-04
So it looks like the file copied, but only 137GB of it, could that have been unused space within the virtual disk?

---

