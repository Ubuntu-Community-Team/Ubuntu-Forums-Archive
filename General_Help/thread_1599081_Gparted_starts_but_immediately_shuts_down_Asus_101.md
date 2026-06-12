---
title: "Gparted starts but immediately shuts down Asus 1015 running Meerkat"
date: 2010-10-17
forum: General Help
---

### Post by marco_polo99 on 2010-10-17
Hi, I've installed 10.10 on my Asus 1015PE and when I went to look at the partition table I couldn't get Gparted to stay open.  When I click on it, it opens the window, says that it is searching then scanning, then the window and program closes.  The window is up for maybe 3 seconds tops.

I've got two other ubuntu netbook versions running on the same machine and gparted works fine on those installs.  I've tried completely removing gparted  and reinstalling, I've rebooted, I've tried calling it from the terminal, but always the same: it opens, starts to scan and closes.  

Any advice?

---

### Post by sikander3786 on 2010-10-17
Please start gparted from terminal and post the output after it crashes.

```
gparted
```

---

### Post by WinRiddance on 2010-11-20
**Re: GParted won't open**                 
                                                            I downloaded Ubuntu Live CD and burned my image day before yesterday, on November 18th.
That's what I'm using at this very moment, to reply to this thread.
Well, guess what? The Gparted in the LiveCD has the same problem, at least on my system ...

Starting Gparted from the Gui shows an attempt which closes after a few seconds by itself.
Starting Gparted with sudo, directly from the terminal, terminates with this message:

> [SIZE=2]======================
libparted : 2.3
======================

glibmm-ERROR **: [/SIZE] [SIZE=2]
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...[/SIZE] [SIZE=2]
ubuntu@ubuntu:~$[/SIZE][SIZE=2]                      [/SIZE]           
I need to work with one of my partitions for restoration & backup purposes. This really bites!

---

### Post by marco_polo99 on 2010-11-28
Since the first posting it has actually succeeded in staying open, but it now thinks that my entire hard drive is unallocated. It has about 15 partitions in it.

"Invalid partition table on /dev/sda -- wrong signature 0.

---

### Post by achmonth on 2010-11-29
> **WinRiddance said:**
> **Re: GParted won't open**                 
                                                            I downloaded Ubuntu Live CD and burned my image day before yesterday, on November 18th.
That's what I'm using at this very moment, to reply to this thread.
Well, guess what? The Gparted in the LiveCD has the same problem, at least on my system ...

Starting Gparted from the Gui shows an attempt which closes after a few seconds by itself.
Starting Gparted with sudo, directly from the terminal, terminates with this message:

[SIZE=2]                      [/SIZE]           
I need to work with one of my partitions for restoration & backup purposes. This really bites!

I get the same error, and it's bugging me like a crazy monkey in my pillow...

---

### Post by sikander3786 on 2010-11-30
See this bug for more info.

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)

It says the issue has been fixed for Maverick. If you are still getting the error, you can open up that bug with all the info needed there.

---

