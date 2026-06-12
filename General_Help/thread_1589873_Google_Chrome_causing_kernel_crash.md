---
title: "Google Chrome causing kernel crash"
date: 2010-10-07
forum: General Help
---

### Post by pdwerryhouse on 2010-10-07
Hi all,

I have an issue with Ubuntu karmic crashing when I use Google Chrome. I had this problem earlier in the year with Chromium, so I switched to Chrome 6 and this was suitable for my needs, and didn't cause the problem.

However, certain websites no longer work properly with Chrome 6 and I've had to upgrade to Chrome 7 - and this is causing the kernel to crash.

Typically it happens when I've got a number of Chrome tabs open, and then I open up a url from a program like Liferea or Pidgin (which thus opens up a new tab in Chrome) and then my screen turns black and the kernel locks up hard. Obviously it's some sort of bug in the kernel, because a userland application shouldn't be causing a kernel to die. Also, as it locks up hard, there aren't any kernel messages in the log files.

My kernel version is linux-image-2.6.31-22-generic on 32-bit Intel.

Anyone know of a solution to this?

I've done some websearches and found that other people have encountered similar problems and for them running Chrome with the --disable-sandbox option fixed the problem for them, but it does not help in my case.

Thanks in advance.

(Please, don't suggest that I upgrade to lucid. I would if I could, but I can't at the moment. Also, no, I don't want to use Firefox or any other web-browser).

---

