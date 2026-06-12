---
title: "Compiz Fusion with Google Chrome"
date: 2010-02-03
forum: General Help
---

### Post by markprice on 2010-02-03
I've been trying to get the dodge animation to work on Google Chrome windows. If I enable "use system titebar and borders" in the Chrome options panel the dodge animation works but but with the default hide titlebar settings I haven't been able to get it to work.

My current window match statement for the dodge animation is:
```
(type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz)
```

Any ideas on how to get this to work?

---

### Post by M@XLOL on 2010-08-13
> **markprice said:**
> I've been trying to get the dodge animation to work on Google Chrome windows. If I enable "use system titebar and borders" in the Chrome options panel the dodge animation works but but with the default hide titlebar settings I haven't been able to get it to work.

My current window match statement for the dodge animation is:
```
(type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz)
```

Any ideas on how to get this to work?

This isn't working for me either and its driving me nuts.

---

### Post by lmellor on 2010-09-15
Hi, I have found the solution to this...

[https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp?hl=en-us](https://chrome.google.com/extensions/detail/elnmibmpefhmfgphdphdncoogpbfmlbp?hl=en-us)

unfortunately (or fortunately depending how you view things) it means swapping the chrome style title bar for a gnome one, follow the instructions given by the 2nd screenshot and hey presto, dodging comes back!

personally I'd sooner have all of my windows use the same style of title bar, it's only an app after all, not an OS (yet).

I hope this is of some help to you guys.

Just incase the page gets removed or changed at any point I simply right clicked the 'grey area' to the right of the open tabs and selected 'Use system title bar and borders'.  The ambience theme really helps to tie things in though, much nicer than any of the default chrome ones I've found on their gallery.

---

