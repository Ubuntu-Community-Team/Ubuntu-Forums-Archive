---
title: "usplash rejecting theme after Karmic upgrade"
date: 2010-02-18
forum: General Help
---

### Post by nabilalk on 2010-02-18
usplash throws the following error on Gateway M-6827 running Karmic (9.10)

> usplash: rejecting theme /usr/lib/usplash/usplash-artwork.so 800x500
(assertion theme->theme_height && theme->text_y + theme->text_height >
theme->theme_height failed); please file a bug

I found a similar launchpad bug with a proposed fix, but could not figure out how to install the fix.

[_bug report_]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/401432") 

[_fix_]("https://launchpad.net/ubuntu/karmic/+source/usplash/0.5.33")

How do I install this fix? Also, I use a custom usplash. Will this usplash fix replace that? Thanks

---

