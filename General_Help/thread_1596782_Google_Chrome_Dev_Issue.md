---
title: "Google Chrome Dev Issue"
date: 2010-10-14
forum: General Help
---

### Post by SoulSmasher on 2010-10-14
Hi, I'm having this issue since yesterday on my Maverick x64,

When I try to run google chrome dev edition, when I type something, it says "Segmentation fault" in terminal and shuts down.

What should be the issue ?

Thanks,

p.s: Plase don't tell me trying using chromium etc. That is not a solution, just an avoidance.

---

### Post by Sub101 on 2010-10-14
Do you mean the beta or the unstable?

---

### Post by SoulSmasher on 2010-10-14
unstable release. But that was nice until yesterday and I didn't update the google chrome. 

So some setting alteartion or the yesterday's update should be the reason.

Just checked, beta version suffers from same issue though.

---

### Post by SoulSmasher on 2010-10-14
This is gdb output:

```
gdb /opt/google/chrome/chrome
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /opt/google/chrome/chrome...(no debugging symbols found)...done.
(gdb) run
Starting program: /opt/google/chrome/chrome 
[Thread debugging using libthread_db enabled]
[New Thread 0x7fffeb7de710 (LWP 9597)]
[New Thread 0x7fffeafdd710 (LWP 9598)]
[9589:9589:11574950881:ERROR:chrome/common/json_pref_store.cc(48)] Error reading Preferences: File doesn't exist. /home/arda/.config/google-chrome/Local State: No such file or directory
[New Thread 0x7fffea7dc710 (LWP 9599)]
[New Thread 0x7fffe9bae710 (LWP 9603)]
[New Thread 0x7fffe93ad710 (LWP 9604)]
[New Thread 0x7fffe8bac710 (LWP 9605)]
[New Thread 0x7fffe83ab710 (LWP 9606)]
[New Thread 0x7fffe7baa710 (LWP 9607)]
[New Thread 0x7ffff7ff8710 (LWP 9608)]
[9589:9589:11574988063:ERROR:chrome/common/json_pref_store.cc(48)] Error reading Preferences: File doesn't exist. /home/arda/.config/google-chrome/Default/Preferences: No such file or directory
[New Thread 0x7fffe73a9710 (LWP 9609)]
[New Thread 0x7fffe6ba8710 (LWP 9610)]
[New Thread 0x7fffe63a7710 (LWP 9611)]
[New Thread 0x7fffe59a3710 (LWP 9612)]
[Thread 0x7fffe59a3710 (LWP 9612) exited]
[New Thread 0x7fffe59a3710 (LWP 9624)]
[New Thread 0x7fffe1167710 (LWP 9626)]
[New Thread 0x7fffe1968710 (LWP 9625)]
[New Thread 0x7fffe01f7710 (LWP 9669)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7fffe01f7710 (LWP 9669)]
0x00007ffff1d49f1a in ?? () from /lib/libc.so.6
(gdb) 
```

Any ideas?

---

### Post by SoulSmasher on 2010-10-14
*bump* any ideas_?

---

### Post by Sub101 on 2010-10-14
The two files dont exist:

/home/arda/.config/google-chrome/Default/Preferences
/home/arda/.config/google-chrome/Local State

So have a check of them?

---

### Post by SoulSmasher on 2010-10-14
Nothing changes sadly.

I even tried stable release. Same

Then I gave up, istalled chromium to see if it was ok, and it has the same issue!

Whenever I type a word into address bar, it crashes down!

I'll try installing ia32libs package, then I'll download 32 bit and retry.

---

### Post by SoulSmasher on 2010-10-14
Edit: found out the problem:

I made a hosts file myself for google banned servers, I was using it for both windows and linux enviroment, and shared with many people. When I fixed it back to original /etc/hosts , it was fixed! I don't know what's the issue though.

here's my modified hosts file, what could be wrong ?

[http://pastebin.com/Di0mwLp0](http://pastebin.com/Di0mwLp0)

---

