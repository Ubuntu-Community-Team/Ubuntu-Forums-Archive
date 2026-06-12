---
title: "Firefox Grays Out, Brings System To A Halt"
date: 2009-07-12
forum: General Help
---

### Post by klausner on 2009-07-12
I'm posting this to a new thread, because the [old one]("http://ubuntuforums.org/showthread.php?t=1203965") got sidetracked into unrelated problems. 

Firefox 3.0.11 is frequently bringing my 8.10 system to a halt for what seems like minutes at a time. The Firefox windows grey-out, and the CPU shows 100% usage. 

This always happens these days trying to access Amazon product pages, always while the browser is doing a fetch from *.images-amazon.com. If the Amazon page doesn't link to *.images-amazon.com (e.g. Amazons home page), there doesn't seem to be an issue.

The problem also happens randomly at other times. Sometimes when I'm not even actively doing anything in the browser!

I've searched the Ubuntu and Mozilla forums without success. Tried all the usual about:config hacks.

Has Firefox become such a resource hog that a laptop with only(!) a 1GHz Pentium-M can't handle it? Am I going to have to abandon Firefox? I've already had to pretty much abandon using Amazon. :(

---

### Post by BetterSense on 2009-07-28
Consistent problem for me as well using Jaunty. I simply cannot go to Amazon.com or my browser freezes. This is rather annoying.

---

### Post by Vaphell on 2009-07-28
try upgrading to 3.5, maybe it is caused by less-than-stellar javascript performance of 3.0 (which taxes CPU)? Adblock and NoScript to filter out unnecessary crap would be nice too.

---

### Post by klausner on 2009-07-28
> **Vaphell said:**
> try upgrading to 3.5, maybe it is caused by less-than-stellar javascript performance of 3.0 (which taxes CPU)? Adblock and NoScript to filter out unnecessary crap would be nice too.

Thanks. Tried 3.5.1, didn't make any difference.

---

### Post by philinux on 2009-07-28
Turn off desktop effects I would suggest.

---

### Post by klausner on 2009-07-28
> **philinux said:**
> Turn off desktop effects I would suggest.

Done long ago.

---

### Post by moster on 2009-07-28
Try booting from USB live Ubuntu to see if you there have problems. If not, then you borked your installation.
clean cache, cookies and everything related.

You can try chromium. For me it is several times faster then Firefox.
[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/~chromium-daily/+archive/ppa")

---

### Post by klausner on 2009-07-28
> **moster said:**
> Try booting from USB live Ubuntu to see if you there have problems. If not, then you borked your installation.
clean cache, cookies and everything related.

You can try chromium. For me it is several times faster then Firefox.
[https://launchpad.net/~chromium-daily/+archive/ppa]("https://launchpad.net/~chromium-daily/+archive/ppa")

I've tried cleaning everything out, and tried reinstalling.

Other browsers (including Chromium) don't have the problem, but also don't have the features FF does.

---

### Post by moster on 2009-07-28
Try disabling adblock on that site. Or maybe some other plugin that is fishy. Just to see what is problem.

---

### Post by QIII on 2009-07-28
Try doing two things:

In the navigation bar, type about:config.

Search for ipv6 and change the value for enabling ipv6 to false.

Then, to be sure that none of your plugins is causing the problem

```
firefox -safe-mode
```

or

```
firefox-3.5 -safe-mode
```

You may also have Flash problems if you have both Adobe Flash and either swfdec or gnash installed.

---

### Post by klausner on 2009-07-28
> **moster said:**
> Try disabling adblock on that site. Or maybe some other plugin that is fishy. Just to see what is problem.

It's not adblock.

---

### Post by klausner on 2009-07-28
> **QIII said:**
> Try doing two things:

In the navigation bar, type about:config.

Search for ipv6 and change the value for enabling ipv6 to false.

Then, to be sure that none of your plugins is causing the problem

```
firefox -safe-mode
```

or

```
firefox-3.5 -safe-mode
```


Disabling IPV6 was one of the first things I tried. I even have it disabled at the system level, since I have no use for it.

> You may also have Flash problems if you have both Adobe Flash and either swfdec or gnash installed.

As I said in the initial post, none of the problematic pages use Flash or play music. I don't have either swfdec or gnash installed.

---

### Post by klausner on 2009-07-28
> **QIII said:**
> 
Then, to be sure that none of your plugins is causing the problem

```
firefox -safe-mode
```

or

```
firefox-3.5 -safe-mode
```

Running in safe mode *seems* to solve the problem (have not tested completely), but disabling first one half of my plugins, and the starting again with the second half disabled fails to isolate a culprit. The problem exists unless ALL are disabled (i.e. safe mode).

---

### Post by carolina on 2009-07-28
I also have this problem **everytime** i upload images to a Yola web - site builder account .

---

### Post by QIII on 2009-07-28
> **klausner said:**
> Running in safe mode *seems* to solve the problem (have not tested completely), but disabling first one half of my plugins, and the starting again with the second half disabled fails to isolate a culprit. The problem exists unless ALL are disabled (i.e. safe mode).

It may be one of those situations where diagnosis involves turning them all off, then on one at a time to find the offender.

You might also check to see if Vino is running (forgive me if you already checked.  That seems to come up a lot.)

---

### Post by klausner on 2009-07-28
> **QIII said:**
> It may be one of those situations where diagnosis involves turning them all off, then on one at a time to find the offender.

You might also check to see if Vino is running (forgive me if you already checked.  That seems to come up a lot.)

Vino is not running. It's installed, but I never use it.

---

### Post by klausner on 2009-08-21
Bump. Desperately seeking a solution. Thanks.

---

