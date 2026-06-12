---
title: "Strange NFS permissions problem??"
date: 2010-01-10
forum: General Help
---

### Post by Bucky Ball on 2010-01-10
Hi All,

Here's a weird one so any and all suggestions gratefully appreciated.

I have setup the desktop as the server and laptop as client using NFS. All works brilliantly: I can drag and drop a file from the server folder mounted on the laptop desktop but when I change the name and try to drag and drop it back again I get this error message:

> Error opening file '/media/LoungeMusic/test.xls': Operation not permitted'test.xls' is a file I have been using just to test I can drag and drop. I have tried others. 'LoungeMusic' is the mountpoint for the server partition.

Here's the odd part. At the error message I hit 'cancel' and close the window. If I then re-open the server folder icon on the laptop the file is actually there after all! Magically appears!

Also, if I try and drag and drop a file to the server that is already on the server I am asked if I would like to replace the existing file (on the server) and when I hit 'replace' it does just that, no error message, everything seems as per normal.

Again, any and all suggestions gratefully received as I am at a loss at this point but will keep digging. :)

---

### Post by Bucky Ball on 2010-01-12
Yep, just set up my desktop and connects with the other desktop (the server) and mounts the partitions fine. But same again: I can drop files from the server to the client but not from the client to the server. I get 'Operation not permitted' when I try to. This one though hasn't gone there after all when I close and reopen the directory. Hmm. 

This is pointing to some problem with my server settings, obviously enough. Or perhaps a problem with host on both the clients ...

---

