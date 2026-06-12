---
title: "Trying to get razerd daemon to work."
date: 2009-06-29
forum: General Help
---

### Post by acorn22 on 2009-06-29
I am trying to get my Razer Deathadder to work properly. I am using a fresh install of 9.04. This is what I have done so far. 

On [this page]("http://bu3sch.de/joomla/index.php/razer-nextgen-config-tool") somebody made a utility for razor mice, which I downloaded using git and installed using the attached readme. Everything worked during the installation and I rebooted.

I opened a console and typed the command for the utility "qrazercfg" and I get this error.

```
acorn22@Minty ~ $ qrazercfg
Failed to connect to razerd socket: [Errno 2] No such file or directory
Is razerd running?
```So how do I start this daemon? Any help would be greatly appreciated.

---

### Post by suzenon on 2009-11-04
Well... i'm googling this damn tool issues for like 3 days with completely no success. Most of the threads i find are outdated or without answers like this one.

As above, i've managed to install razercfg following readme instructions, but after instalation... daemon wasn't working.

I had same error. I've added some lines from readme to xorg.conf. Then i started typing **razerd start**, **/etc/init.d/razerd start **in console, as me and as root (sudo) and get this error when typing razercfg:
```

/usr/local/bin/pyrazer.py:23: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Failed to connect to razerd socket: [Errno 111] Connection refused

```Now, after few reboots, the tool is suddenly working. No clue how, no clue why, no clue if it will work after next reboot.
Thing is it's configuration possibility is pretty much poor, screenshot was showing a little bit more. All i can config is scan frequency , dpi and glowing logos. I was hoping to at least change sensitivity . 

So my guess is, to tweak mice sensitivity i'll have to do some changes in xorg.conf?

---

### Post by sparhawkthesecond on 2012-03-05
I know this is an ancient thread, but it's one of the three hits when you Google this error message. And the only one in English.

The solution (from [here)]("http://ubuntuforums.org/showthread.php?t=1578998&page=2") is ```
$ sudo ldconfig
``` Then restart (or run razerd manually), and razerd will start properly, and qrazercfg should run properly.

---

