---
title: "Massive Compiz/Unity/X problems"
date: 2011-10-25
forum: General Help
---

### Post by OboeNerd on 2011-10-25
Hey, I'm having several problems which are greatly affecting the usability of Ubuntu for me.  I would like to see how many people are having the same problems and see whether a bug report(s) are needed.

I am having the following problems:
[LIST=1]
[*]Whenever compiz closes, X segfaults and crashes.
[*]Whenever I click "shutdown", I get logged off instead of a proper shutdown.  Probably related to #1.
[*]Enabling/Disabling most plugins in ccsm crashes Compiz.  See #1.
[*]Opening enough Youtube (or other flash) videos crashes X.
[/LIST]

I am using the ATI proprietary drivers, using the package directly from ATI's website.

Xorg.0.log backtrace:
```
(vdso) (__kernel_rt_sigreturn+0x0) [0xde340c]
```


As per the ccsm problem, it's been reported sparsely:
[https://bugs.launchpad.net/bugs/685552](https://bugs.launchpad.net/bugs/685552)


Is anyone else getting any or all of the above?

Thanks.

---

