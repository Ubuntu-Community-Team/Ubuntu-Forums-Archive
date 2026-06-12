---
title: "VBox memory leak?"
date: 2010-06-02
forum: General Help
---

### Post by blur xc on 2010-06-02
I'm running Vbox 3.2, ubuntu 10.04 64bit host, Vista guest, and noticed something odd the other night.  I should mention that I just recently switched to 64bit, was previously on 9.04 32bit.  

When I booted up, my conky showed that I was using just under 500mb of ram.  When I fired up the VM, it jumped to about 2gigs, which makes sense because I have my guest configured to use 1.5gigs of ram.  I used it for a bit, left it idle while I watched a show with my wife, and about and hour or so later I came back to it and my conky now showed that I was using 3.7gigs of ram.  Is this a memory leak?

Is this a bug?  Should I hit up the VBox folks?  I'm also running 3.2 at work on a 64bit Win7 host, but haven't noticed any problems.

Thanks,
BM

---

### Post by blur xc on 2010-06-04
Apparently this was a known bug and is fixed in the latest version of vbox...

All seems well.

BM

---

