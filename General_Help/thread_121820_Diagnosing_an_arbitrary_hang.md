---
title: "Diagnosing an arbitrary hang"
date: 2006-01-26
forum: General Help
---

### Post by mabster on 2006-01-26
I had my first Linux hang today and I'm trying to determine how to diagnose what happened.  I should point out that I'm fairly new (2 weeks) to Linux so I'm really startinng this from a fairly noobish standpoint.  I've been running the same setup for a while now without any issues (though there was a new kernel security update about a week ago IIRC).

While I was surfing the web using Mozilla, everything just locked up, including the mouse.  I tried switching across to another virtual console but to no avail.  The last thing I had done before the crash was to open a link in a new tab (it had started to load).

After I had restarted my machine I dmesg'd and checked /var/log/Xorg.0.log but there weren't any error messages.  Are there other places I could look to find anything that could possibly cause a hang like this?

I am running this on a laptop (though I don't think this is laptop specific).  It's an Inspiron 5150.  For reference:

```
mabster@mab:/var/log$ X -version

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux mab 2.6.12-10-686-smp #1 SMP Mon Jan 16 18:39:17 UTC 2006 i686
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-686-smp (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Mon Jan 16 18:39:17 UTC 2006 T
```

---

### Post by adwait on 2006-01-26
Maybe firefox just went overboard with memory usage or something. Happens sometimes. Its possible that only Gnome crashed and not your entire Linux kernel. Did you try hitting Ctrl+Alt+Backspace? (That restarts Gnome or whatever window manager you are using). Or Ctrl+Alt+F1 (gets you a console).

---

### Post by mabster on 2006-01-27
Yeah, I tried Ctrl-Alt-F1 and nothing happened :-/

---

