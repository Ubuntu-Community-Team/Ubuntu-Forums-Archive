---
title: "Huge UUID file in gvfs-metadata - 8.4 gigs - Help??"
date: 2010-02-14
forum: General Help
---

### Post by ZhuaSD on 2010-02-14
Hi all, I just began having a problem, hope someone can help.

I have a UUID file that has grown to 8.4 gigs...

and I don't know what to do.  Its sucking up all the free space in the partition.  

I guess I will have to delete the file but I don't know how to do it properly.

I suspect this is a backup of all the data I have been moving around between drives recently.

Any advice?  Please?  :D  :popcorn:

---

### Post by ZhuaSD on 2010-02-14
Hoo boy.  I know which partition it is, and I can't unmount any of my partitions now.  I just restarted once to try and clear things out, but it did'nt seem to work.  Will try that again.

---

### Post by ZhuaSD on 2010-02-14
Well, problem solved.  

Just in case it helps anyone, I had two files listed as unknown in my gvfs-metadata folder:

uuid-9124-115A.QRQ37U   ---this is the big one
uuid-9124-115A          --- this one is normal sized but still unknown

So I deleted both of them while the partition was not mounted, re-started, and all is well.  

;-)

---

