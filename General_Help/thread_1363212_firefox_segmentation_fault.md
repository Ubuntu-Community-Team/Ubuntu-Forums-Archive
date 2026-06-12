---
title: "firefox segmentation fault"
date: 2009-12-24
forum: General Help
---

### Post by thirddeep on 2009-12-24
I just updated Firefox, and now get a segmentation fault whenever I try to run it.

Ubuntu : 9.04
Arch   : x86
Kernel : 2.6.30-02063003-generic
Firefox: 3.0.16+nobinonly-0ubuntu0.9.04.1
Source : Standard repository

Problem occurs when :
```
$ firefox
Segmentation fault
```

That segmentation fault is instant.  There are no FF processes listed before or after I ran firefox.  See ff_strace.txt for those that can understand strace output.

Solutions tried:
1) Re-install
2) Uninstall / install
3) Removed .mozilla
4) Reboot
5) Google -> lol, 10 Mil hits.

Any help would be appreciated :-)

Thd.

---

### Post by Soul-Sing on 2009-12-24
1) could be an add=on
2) could be "scim" related problem, not likely though

---

### Post by thirddeep on 2009-12-24
How do I remove add-ons when FF is not working ? I take it add-ons are dumped in some directory ?

I just removed SCIM and components (I had to look up what it is, and I don't think I need it), still same problem.

Thd.

---

### Post by Soul-Sing on 2009-12-24
please try: /home/<yourname>/.mozilla/firefox/nf349dl4.default

---

### Post by thirddeep on 2009-12-24
I deleted my entire .mozilla directory.  Starting FF, it segfaults so quick it does not even create a new .mozilla.

Thd.

---

### Post by Soul-Sing on 2009-12-24
> **thirddeep said:**
> I deleted my entire .mozilla directory.  Starting FF, it segfaults so quick it does not even create a new .mozilla.

Thd.

I should file this case as a bug on launchpad. weird.
try a complete reinstall of firefox....(which you already did i assume?)

---

