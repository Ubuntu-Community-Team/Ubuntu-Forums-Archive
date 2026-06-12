---
title: "High temp with Firefox"
date: 2011-08-17
forum: General Help
---

### Post by northwestern on 2011-08-17
Could anybody explain the difference in cpu temperature between Firefox 6 & Chrome. My computer is an HP laptop (DV5) running Ubuntu 11.04, at the moment running Chrome the temperature stays stable at 48 deg C but running Firefox the temperature reaches 62 deg c.
Anybody else noticed the difference and found a cure ?.

Regards
Northwestern

---

### Post by northwestern on 2011-08-17
Thanks for your reply,it seems to be definitely Firefox 6 that is causing the problem. Where and who do I log this possible bug too.

Northwestern

---

### Post by lovinglinux on 2011-08-17
First, you need to make sure you comparing both browsers with the same web pages open. For instance, if you open a page with Flash content, CPU usage and temperature will be higher.

I recommend using [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") to prevent unnecessary flash content from loading.

If you are opening the same pages on both browsers and without flash, then check if the problem is caused by an add-on. To do that, start Firefox in safe mode with:

```
firefox -safe-mode
```

---

