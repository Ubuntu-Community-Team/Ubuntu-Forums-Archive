---
title: "Am I a 64 or 32?"
date: 2011-03-30
forum: General Help
---

### Post by luiznetto on 2011-03-30
Hi all,

I just got this

[http://www.google.com/chrome/eula.html?brand=CHKD&utm_campaign=en&utm_source=en-oa-na-us-N5295.130861.TECHMEDIA&utm_medium=oa&installdataindex=homepagepromo](http://www.google.com/chrome/eula.html?brand=CHKD&utm_campaign=en&utm_source=en-oa-na-us-N5295.130861.TECHMEDIA&utm_medium=oa&installdataindex=homepagepromo)

while I was browsing on my Firefox 3.0.15, Ubuntu 8.04. It invites me to install the new Chrome browser, and it asks a simple question, as you can see: do I want to install the 32 bit .deb or the 64 bit .deb package?

Well, I installed this Hardy Heron on my Aspire 5315 laptop long ago, and I don't really know whether I have a 32 or a 64 bit system. uname doesn't give me that info; I tried dmesg | grep bit, but still no clue.

I also found this:

[http://www.google.com/support/forum/p/Chrome/thread?tid=76937011a558491e&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=76937011a558491e&hl=en)

which seems to be a warning, so I am confused. Which version of Chrome should I install (if any at all)?

Thanks in advance,
Luiz

---

### Post by bleedingsamurai on 2011-03-30
try
```
uname -a
```
this should give you more information then just uname you should see x86 or x86_64

---

### Post by luiznetto on 2011-03-30
I did this, and my output is

$ uname -a
Linux luiz-laptop 2.6.24-25-generic #1 SMP Tue Oct 20 07:31:10 UTC 2009 i686 GNU/Linux

---

### Post by oldfred on 2011-03-30
[LEFT]You are 32bit.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
32 or 64 bit
uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit

[/LEFT]

---

### Post by luiznetto on 2011-03-31
Yes, this answers my question. Thanks a lot.

Luiz

---

### Post by jerome1232 on 2011-03-31
I just wanted to clarify, That means you are running 32 bit Ubuntu.

But was your question "Am I running a 32 or 64 bit OS?" or was your question "Is my processor 32 or 64 bit?"

If you asking about your os than yes you are running a 32 bit OS.

If you are asking about your cpu than most probably it is 64bit, to check you can do this, if there's output your cpu is 64 bit, if not it's 32 bit.

```
grep lm /proc/cpuinfo
```

---

### Post by luiznetto on 2011-03-31
Yes, I did this, and I really have a 64 bit processor, but a 32 bit Ubuntu installed on my hard drive.

Thanks again,

Luiz

---

