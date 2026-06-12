---
title: "Ubuntu 11.10 Java Buggy With Yahoo Games"
date: 2012-02-18
forum: General Help
---

### Post by ep_ on 2012-02-18
Yahoo games using Java generally works as expected but it's only a matter of time before the game windows go blank (solid gray) and become unresponsive.  I'm 64 bit and this happens using both Chromium and Firefox.

I'm guessing installing Sun/Oracle's latest Java might solve this issue.  However, this is not a user-friendly task and I don't believe I'd get automatic security updates using this solution, if indeed it is a solution.

Here's what I'm using:

Kubuntu 11.10

3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

Chromium 16.0.912.77 (Developer Build 118311 Linux) Ubuntu 11.10
Firefox 10.0.2

Any solutions?

---

### Post by Paddy Landau on 2012-02-19
I can't tell you why that happens. However, it does seem possible that your memory may be insufficient. What RAM do you have installed?

Sun Java has been replaced with Iced Tea (Open Java) because of new problems with Sun. However, if you want to try it, first deinstall Iced Tea; then download Sun Java and install it.

If it doesn't work, you can deinstall it and reinstall Iced Tea to revert.

---

### Post by ep_ on 2012-02-26
I have 2 gigs of RAM.  This happens in yahoo dominos and chess.

---

### Post by Paddy Landau on 2012-02-27
Sorry, I don't know. Have you tried replacing Icedtea with Sun Java? If you do that, it should help you know whether it's a problem with Icedtea or with the program itself. Or maybe something else.

---

### Post by Gremlinzzz on 2012-02-27
java sun update:popcorn:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)


copy and paste

---

