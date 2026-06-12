---
title: "Upgrade to 10.04 still has 9.10 bootsplash"
date: 2010-04-30
forum: General Help
---

### Post by agarciamog on 2010-04-30
Greetings all,

I recently upgraded to 10.04 from 9.10. Everything looks fine except for the fact that I still get the old boot splash from 9.10. Any suggestions?

-Alberto

---

### Post by claustin on 2010-04-30
Yes, I upgraded from 9.10 to 10.04 last night and have this exact issue.  Have you found a solution yet?

---

### Post by agarciamog on 2010-04-30
No, no solution as of yet.

Guys?

---

### Post by wojox on 2010-04-30
Have you rebooted a couple times?

---

### Post by ranch hand on 2010-04-30
If you have checked to make sure that plymouth and libplymouth2 are installed you could try running'
```

sudo update-initramfs -u

```
This should have been run when you upgraded.  Maybe it didn't.

You might also want to check to see what version you are actually running.  A quick look at "system monitor" under the "system" tab  will have it listed.

---

### Post by simon_r on 2010-05-04
Hi all,

Have found a lot of fixes on these forums but have never actually posted, was having this issue and found a fix so figured I'd finally contribute..

Tried all suggestions, however what this came down to in my case was xsplash was still installed (I had some black screen issues during the upgrade process and ended up ultimately having to do 'dpkg --configure -a' to repair things, still though not entirely sure why xsplash was left)..

Anyway, once I removed all the xsplash packages and reinstalled all the plymouth packages everything is now as it should be.

Si.

---

