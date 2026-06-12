---
title: "firefox 6 &amp; 7 : resource hog and completely slows down the computer"
date: 2011-10-19
forum: General Help
---

### Post by 13east on 2011-10-19
firefox 6 & 7 completely slows down my computer after few minutes of use.  RAM usage skyrockets 90% (out of 3.7 gb) with firefox using over 2.7 gb of ram for itself.

under Kubuntu 11.04, i was able to roll back to firefox 5 and saw no slowdown in computer's performance.  with 11.10, no option is given to roll back firefox to an earlier version.

is there a way to fix firefox from being such a vast resource hog?  

if not, is there a way to roll back to firefox 5 in kubuntu 11.10?  where can i find a .deb file for firefox 5?

---

### Post by Meelad on 2011-10-19
Installing chrome would also be an option.. It's really fast, but Firefox has more plug-ins.

---

### Post by 13east on 2011-10-19
> **Meelad said:**
> Installing chrome would also be an option.. It's really fast, but Firefox has more plug-ins.

i like chrome.. but there are some plugins that are not avaliable w. chrome that i have become addicted to while using firefox

---

### Post by lovinglinux on 2011-10-19
Please start Firefox in safe mode and report if the problem persists.

```
firefox -safe-mode
```

If yes, then you need to find out which extension is causing the problem. If not, create a new profile.

```
firefox -P
```

---

