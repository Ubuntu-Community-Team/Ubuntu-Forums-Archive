---
title: "No readline.h - Differences in an install"
date: 2011-01-14
forum: General Help
---

### Post by tantooga on 2011-01-14
Sort of an odd general question here. I signed up for a programming class that programs in Linux, and since I use Windows normally I installed vmware player so I could use both at the same time. I installed 64-bit Ubuntu. On the first assignment I needed to compile something that uses readline.h. Compiles fine. 

Few days later I decide to go for 32-bit Ubuntu instead (seeing as how I'm only letting it use a gig of ram anyway), install another virtual machine, all seems good. I go to compile this code again and I get an error that I don't have readline.h. I look in usr/include and sure enough, no readline.h. Just to amuse myself I check the include folder on the 64-bit VM; amazingly there it is.

Now I know where I could get the readline header file, that's not the issue here. The issue is there's considerably fewer header files in the 32 bit include folder than in the 64 bit one. Any thoughts why? Is this something built into Ubuntu, or does it have something to do with that VMWare Tools installed both versions of Ubuntu for me? I'm concerned about what else I might be missing.

---

