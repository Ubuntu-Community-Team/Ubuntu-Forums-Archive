---
title: "Broken libkonq.so.5"
date: 2010-06-14
forum: General Help
---

### Post by MrSergeiMosin on 2010-06-14
I have a new install of Kubuntu 9.10. Everything works, with the exception of Konqueror and Dolphin. When I try to run them from the menu, they never start. running them from a terminal results in the following output for both:

> : error while loading shared libraries: /usr/lib/libkonq.so.5: file too short

The following has not worked:

aptitude reinstall libkonq5
aptitude install -f
aptitude install -f libkonq5
aptitude remove dolphin, aptitude purge dolphin, aptitude install dolphin
aptitude remove konqueror, aptitude purge konqueror, aptitude install konqueror

All of the above also fails using apt-get. Manually installing the above packages also fails.

Is it safe to uninstall and reinstall just the libkonq5 package? or is there some other way I should be going about this?

---

