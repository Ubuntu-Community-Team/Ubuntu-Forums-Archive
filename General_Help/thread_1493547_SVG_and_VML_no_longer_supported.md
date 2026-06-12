---
title: "SVG and VML no longer supported??"
date: 2010-05-26
forum: General Help
---

### Post by PerfectReign on 2010-05-26
I had an issue where I upgraded to 10.04 from 9.1.  I went back to 9.1 (fresh install) and am now using the firefox-cum-namroka browser.

I went to a mapping site I've used often.  In fact, I was just there last week on 9.1 before upgrading.

I now get the message, "Your Web browser does not support SVG or VML. Some graphics features may not function properly."

???

about:config shows svg being enabled.

Any ideas?

---

### Post by PerfectReign on 2010-05-26
Okay, I found a fix.

It is VERY annoying that this took place and without any forewarning.

Here's what I did. I installed user agent switcher.  I then imported user agents (grabbed from here: [http://techpatterns.com/forums/about304.html](http://techpatterns.com/forums/about304.html) ) and set my browser to Firefox 3.5 (Linux).  

The SVG files load fine. I think the javascripting on the site was reading my browser as this bizarre naoroka and not knowing what to  do.

---

