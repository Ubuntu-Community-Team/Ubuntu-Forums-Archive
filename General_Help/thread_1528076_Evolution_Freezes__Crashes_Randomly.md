---
title: "Evolution Freezes / Crashes Randomly"
date: 2010-07-10
forum: General Help
---

### Post by jerremy-tamlin on 2010-07-10
I have tried four times to submit this bug report to Launchpad and each time it has failed. So I'm posting it here in the hope that someone can help me.

**Package Hint:** Evolution 2.28 libetable.so.0.0.0

**Bug Description:**
I started Evolution with the command "evolution --debug=~/Desktop/evolution_debug.txt --disable-eplugin" and Evolution started but was frozen. ie it would not respond to mouse clicks or key presses.
I killed it by pressing CTRL-C in the terminal from which I had started it.
I started Evolution again with the same command and this time it worked as expected for a few minutes until I happened to click the checkbox (to hide) one of my Google Calendars. When I did so Evolution Crashed.
The Terminal Output is attached.

I started Evolution a third time to submit a bug report using "Submit Bug Report" from the Help Menu.
When I tried to submit this bug an unnamed messagebox appeared with the text "Unable to create the bug report: Product or component not specified." Bug Buddy then closed.

dmesg contains the following two lines:
```
[73294.125453] evolution[775]: segfault at 0 ip 008d9899 sp bfe9c790 error 4 in libetable.so.0.0.0[8c4000+71000]
[73985.441931] evolution[1276]: segfault at 0 ip 0014df6c sp bfc24400 error 4 in libetable.so.0.0.0[110000+71000]

```
There are three libetable.so.0.0.0 files on my computer:
```
338527 -rw-r--r-- 1 root root 1462845 2010-06-09 19:33 /usr/lib/debug/usr/lib/evolution/2.28/libetable.so.0.0.0
312290 lrwxrwxrwx 1 root root      18 2010-07-10 16:52 /usr/lib/evolution/2.28/libetable.so.0 -> libetable.so.0.0.0
311836 -rw-r--r-- 1 root root  469336 2010-06-09 19:33 /usr/lib/evolution/2.28/libetable.so.0.0.0

```
The debug file appears to be different
(Note: I don't understand the diff command and wonder if perhaps two binary files are always different?)
```
:~$ diff /usr/lib/debug/usr/lib/evolution/2.28/libetable.so.0.0.0 /usr/lib/evolution/2.28/libetable.so.0.0.0 
Binary files /usr/lib/debug/usr/lib/evolution/2.28/libetable.so.0.0.0 and /usr/lib/evolution/2.28/libetable.so.0.0.0 differ

```

---

