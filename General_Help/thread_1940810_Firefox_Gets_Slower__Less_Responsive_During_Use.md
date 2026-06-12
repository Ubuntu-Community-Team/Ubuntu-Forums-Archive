---
title: "Firefox Gets Slower / Less Responsive During Use"
date: 2012-03-14
forum: General Help
---

### Post by bsntech on 2012-03-14
Hello all,

I have two completely different systems running Ubuntu 11.04.

Firefox version is 10.0.2

When I first open Firefox for regular browsing, it is fast without any problems.

However, after maybe an hour or so of use and opening/closing tabs here and there, Firefox gets slower.  I'm surprised that I couldn't find another thread on this issue; some were similar but still off.

First system runs an Intel CPU and Intel graphics card.  Second system runs an AMD CPU and has an ATI graphics card.  I am using the standard graphics driver on the computers - I'm not using the proprietary one (although this really doesn't have anything to do with the issue).

Browsing is fine and it just gets slower as I try to switch tabs or click on links, type in boxes, or submit forms.

It has been doing this for weeks now - and I attribute it to the last upgrade of Firefox myself.  There has been at least one kernel update since the problem occurred, and when upgrading to the newer kernel, the problem continued.

This only affects Firefox - nothing else.

Just wanted to see if anyone else has seen this problem as well.

---

### Post by lovinglinux on 2012-03-15
Most likely that Firefox is leaking memory. Check if memory usage goes too high when the problem occurs. You can do that with System Monitor. If it does, try Firefox in safe mode for a while. 

```
firefox -safe-mode
```

If the problem goes away in safe mode, then most likely an extension is causing the leak. You need to test them individually to find the culprit.

---

