---
title: "Firefox &quot;Report a Problem&quot; does not work."
date: 2011-10-20
forum: General Help
---

### Post by csh on 2011-10-20
OS: Xubuntu 11.10 64 bit, Windows 7.

There is a website, when browsing in Windows OS, it works well in Firefox. However, when using Xubuntu, that website only work well with Google Chrome but not firefox. So, I am trying to report this problem.

But, when using Firefox in Xubuntu, I tried to click Help -> "Report a Problem", nothing happened.

How to solve this problem? Is this a bug?

---

### Post by gsmanners on 2011-10-20
With Xubuntu, it's a bit more difficult. You have to go to terminal and type:

```
apport-bug firefox
```

Or, if you have a strong aversion to terminal you can go here:

[Report a bug]("https://launchpad.net/ubuntu/+source/firefox/+filebug")

---

