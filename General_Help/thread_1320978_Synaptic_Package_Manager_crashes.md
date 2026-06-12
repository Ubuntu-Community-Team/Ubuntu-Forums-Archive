---
title: "Synaptic Package Manager crashes"
date: 2009-11-09
forum: General Help
---

### Post by jbohn on 2009-11-09
Hello,

I'm running 9.04 on a MacBook 4,1 and life has been wonderful- until now.  For some reason, Synaptic Package Manager now crashes (grays out) every time I run it.  I searched the forum, but didn't find anything that seemed to pertain to this specific problem.

Any ideas?

Thanks!!

---

### Post by wojox on 2009-11-09
You using Virtualbox?

---

### Post by jbohn on 2009-11-09
Nope.  Just a normal install of 9.04 as the sole OS on this box.

---

### Post by michy99 on 2009-11-09
Start it from a terminal.```
gksudo synaptic
```When it crashes, copy the error message and paste it here.

---

### Post by jbohn on 2009-11-09
No error messages.  Just grays out.  I finally closed the terminal window to kill the process, and closed the synaptic window, which just says it isn't responding, without being more specific than that.  :confused:

---

### Post by jbohn on 2009-11-10
Hmmm... read the man page, and tried gksudo -d .  Here's what I got:

> ^[[Ajbohn@jbohn-laptop:~$ gksudo -d synaptic
No ask_pass set, using default!
xauth: /tmp/libgksu-9e71ON/.Xauthority
STARTUP_ID: gksudo/synaptic/3902-0-jbohn-laptop_TIME122001
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...


...and then it comes up, but grays out.

Now here's where it gets strange.  When I finally ^C to get my terminal prompt back, synaptic starts working, and seems to work fine until next restart.  I'm glad it works (sort of), but I'd like to know why...

Any more ideas?

Thanks!

Edited to add: apparently, I spoke too soon.  Seems now only to work fine until the authentication times out (see below).

---

### Post by jbohn on 2009-11-10
Noticed one more thing.  On initial launch, everything looks good until the "Starting Administrative..." disappears from the bottom panel, which is when it grays out.

Is it maybe a problem with the authentication?  I read somewhere in the forum a guy having problems with this after he set up a fingerprint reader. None of those here, but maybe related?

---

### Post by maverick340 on 2011-03-03
Remove the apt-xpian-index package complete by 
```
sudo apt-get remove --purge apt-xapian-index
```
Then reinstall it by 
```
sudo apt-get install apt-xapian-index
```

That should fix the quick search segfault/crashing error in synpatics package manager.

---

### Post by arpit22x on 2011-04-25
I am facing the Similar problem in synaptic. When I try to change proxy settings, it crashes. help please!!

---

