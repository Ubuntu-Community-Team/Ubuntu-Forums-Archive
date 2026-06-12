---
title: "Ubuntu 10.4 Won't run &quot;application/x-executable&quot;"
date: 2010-03-26
forum: General Help
---

### Post by GS-R on 2010-03-26
OS Ubuntu 10.4
Over the past 2 weeks i have been trying to get this "application/x-executable" (netpanzer 0.8.3) file to run. But have had no luck yet. I know in the software centre that you can get "netpanzer 0.8.2". But it is not the latest version. 

Also when i was running Mandriva 2010 FREE edition it could run the "application/x-executable".
So could someone help me?

---

### Post by cdenley on 2010-03-26
Are you trying to run a 32-bit binary on a 64-bit system. If so, you will definitely need 32-bit libraries.
```

sudo apt-get install ia32-libs

```

Or maybe it just isn't compatible. Either way, I always recommend users stick to the repo. When you start messing with third party software like that, you sacrifice security, stablity, compatibility, and manageability.

---

### Post by GS-R on 2010-04-16
Yes i solved it.
I just went to Package Manger and downloaded Sdl mixer.
And yes i was using a 64bit computer. But the same thing happed on my 32bit computer [which was Ubuntu 9.10].
\\:D/

---

