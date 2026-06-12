---
title: "Random Crashes"
date: 2010-03-20
forum: General Help
---

### Post by rex_the_first on 2010-03-20
Hi,

I upgraded my HP 2133 laptop to Xubuntu 9.10 and having fun with Pulseaudio (and eventually giving up, ALSA on its on will do for me) I now have a new issue.

-The problem-
The laptop crashes randomly.  It has crashed just after logging in before it finished loading.  When I was trying to connect to the internet.  When I opened System Update, e.t.c.  Not every time but it is very annoying.
------

I have run memtest and done a simple disk check.  Do you have any idea if / where in the logs I should be looking or should I be doing more hardware testing?  It did not happen in 9.04 so I thought it was a buggy module but I am not sure, it seems to be getting worse so maybe something is on the way out.

Cheers,

---

### Post by syrex314 on 2010-03-21
What happens when the computer crashes? Does it just hang? Does it suddenly restart?

Have you examined /var/log/messages ?

---

### Post by woodmaster on 2010-03-21
If you can still move the mouse after it hangs, it's graphics crashes check this out. It worked for me
:smile:
[*[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=789578 [/COLOR]*]("http://http://ubuntuforums.org/showthread.php?t=789578")
Hope it helps

---

### Post by lyall on 2010-03-21
read this about random crashes **DebuggingSystemCrash**
[https://help.ubuntu.com/community/DebuggingSystemCrash]("https://help.ubuntu.com/community/DebuggingSystemCrash")

have you checked your hard drive, it might be the problem.
see **TestingStorageMedia**
[https://help.ubuntu.com/community/TestingStorageMedia]("https://help.ubuntu.com/community/TestingStorageMedia")

Smartmontools [https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

good luck and have fun learning

---

### Post by rex_the_first on 2010-03-22
Thanks very much.  Some quick answers.
It is a full system crash (e.g. the caps lock key light doesn't change when Caps is pressed) and mouse defiantly isn't working.  I have run memtest over night and it said my RAM was clean.  I have checked my hard drive:
```
sudo touch /forcefsck
```
but I am abroad with only my laptop so can't do a bad sector scan but I will use Smartmontools and post here if I find anything.

I checked the kernal log and it seems I've got a minor [ALSA bug]("https://bugzilla.redhat.com/show_bug.cgi?id=527538") but apart from that there is nothing.  The system usually crashes when I'm not listening to audio so I very much doubt it is ALSA related.  I still think it is a buggy module but var/log/messages and kernel come up blanks...

Cheers and any more thoughts?

---

