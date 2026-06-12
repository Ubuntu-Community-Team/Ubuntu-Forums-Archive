---
title: "How do I revert to an older package version?"
date: 2011-05-10
forum: General Help
---

### Post by turqoisehex on 2011-05-10
Hi,
I'm trying to get MAME and GMAMEUI to work on Maverick, and running into challenges. I'm able to *run* games no problem, but as soon as I try to go to Options --> GMAMEUI preferences, GMAMEUI crashes.

I checked with [http://gmameui.sourceforge.net](http://gmameui.sourceforge.net), and it says GMAMEUI is only compatible up to MAME 0.123; the version in the repositories is 0.139 :(

I would like to try reverting to an older version of MAME (0.123) to see if that changes anything. I followed these instructions for using Apt Preferences:
[http://dimitar.me/ubuntu-revert-to-an-older-version-of-a-package](http://dimitar.me/ubuntu-revert-to-an-older-version-of-a-package)

But adding ```
Package: mame*
Pin: version 0.123*
Pin-Priority: 1001
```
to /etc/apt/preferences did nothing.

Any help, either on revering MAME or troubleshooting GMAMEUI, is very much appreciated.:KS Thank you

---

