---
title: "Chromium Eating Ram"
date: 2010-07-09
forum: General Help
---

### Post by Socialsymbol on 2010-07-09
I use Chromium because of how buggy flash currently is in Firefox.

So far I love Chromium, it's fast and has no problems with any of the sites I go on. The one major drawback however is it seems after having Chromium open for an extended period of time (~40 min+) it starts to use obscene amounts of RAM (200MB+)

I'm on 64bit Ubuntu 10.04.

---

### Post by sl33tz0r on 2011-02-24
the problem is not about eating ram actually. the problem is about not freeing it. yes, we all know about the different approach to tabs that chrome has. but even when you close it, ram is still used. I have MM 10.10 on a 1gb ram netbook, and when it goes over 900megs I just restart it. if I dont, it just eats all available ram and system freezes. happened quite a few times, so this really is an issue

---

### Post by danjahner on 2011-02-24
A good way to evaluate where the memory is being used in Chrome/ium is by opening the browser task manager by pressing shift+esc. Each of the extensions and tabs is broken out as a separate process with memory and cpu usage. 

This will show you if flash is the major culprit. You can lessen flash dependency a bit by enabling html5 video on youtube. 

[http://www.youtube.com/html5]("http://www.youtube.com/html5")

---

