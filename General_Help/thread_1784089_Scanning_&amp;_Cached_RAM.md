---
title: "Scanning &amp; Cached RAM"
date: 2011-06-16
forum: General Help
---

### Post by astrobob.tk on 2011-06-16
I was wondering why the chached RAM doesn't decrease at the same rate or near that when scanning is done & the scanning software is closed as it increases during scanning ?

When the cached ram reaches a certain point while scanning, the software crashes & I loose my scans :S

Is there any solution to that ?

thanks

---

### Post by ajgreeny on 2011-06-16
I can only suggest that you start whatever program you are using to scan (xsane, simple scan, etc) in terminal.  You may get some error message that helps solve your problem.  It's certainly not a problem I have heard of before, and assuming this is not on your debian machine with just 256 MB ram, you appear to have plenty of ram.  What about swap partition size?

---

### Post by astrobob.tk on 2011-06-16
> **ajgreeny said:**
> I can only suggest that you start whatever program you are using to scan (xsane, simple scan, etc) in terminal.  You may get some error message that helps solve your problem.  It's certainly not a problem I have heard of before, and assuming this is not on your debian machine with just 256 MB ram, you appear to have plenty of ram.  What about swap partition size?

No way would I scan on the desktop lol. I'm using the Studio XPS w/ a swap of 5 GB

for example, here's what free -m shows:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3987       3496        490          0         14        355
-/+ buffers/cache:       3126        860
Swap:         4767       1322       3445

```

I am still scanning (though I already saved what I was scanning before & closed gscan2pdf & am now scanning something new) & used RAM is ~80% of total.

I hadn't had a crash today yet, but previously at some point in the 80% of RAM used, i guess, gscan used to crash; besides sometimes I can't load a .tiff i saved using gscan. It hangs.

---

### Post by ajgreeny on 2011-06-17
You are using a huge amount of ram for just a simple scanning job, surely.  How are you doing it, and why would it use 3GB ram plus another 1+GB swap;  it seems as lot to me.

What exactly are you doing?

---

### Post by astrobob.tk on 2011-06-17
> **ajgreeny said:**
> You are using a huge amount of ram for just a simple scanning job, surely.  How are you doing it, and why would it use 3GB ram plus another 1+GB swap;  it seems as lot to me.

What exactly are you doing?

Well, yesterday I finished scanning without a hitch; no crashing this time.

As for why that much ram, well am here for this too. I am not sure why this is so.
I just launch gscan2pdf, put in the papers to be scanned (individually) & click scan, that's all. The settings im using is 600 dpi

Well it's not just scanning; I also had banshee, opera, thunderbird, OOo Writer & LyX all open lol, but nevertheless it does take that much ram even if im just scanning.

This is what I see now after a new log in. All that's running is banshee, opera & gscan2pdf (nothing scanned yet):

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3987       2694       1292          0        235       1133
-/+ buffers/cache:       1325       2661
Swap:         4767          0       4767

```

Even now, there's enough ram being used.

As for the swap, I am not exactly sure but I believe I had it on hibernate yesterday before scanning.

P.S.: Every time I login after a shutdown, banshee or rhythmbox hang & so does the volume control (i can't control them from the touch controls above the keyboard) until a few minutes.

---

### Post by astrobob.tk on 2011-10-18
I thought of adding the following link for guys that, like me, misunderstand the free -m command output: [http://www.chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://www.chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

