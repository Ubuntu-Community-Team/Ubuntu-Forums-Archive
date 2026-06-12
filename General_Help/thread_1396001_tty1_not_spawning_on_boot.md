---
title: "tty1 not spawning on boot?"
date: 2010-02-01
forum: General Help
---

### Post by calverton on 2010-02-01
Hello all,

I have an interesting problem that sprung up the past few days.  My Ubuntu 8.04 LTS install boots fine, starts all the services as usual, but then says "Loading, please wait...".  I boot to runlevel 2 - straight to the console.

Originally, I had the exact same same error output as this person: [http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/](http://www.mattcutts.com/blog/ubuntu-freeze-no-resume-image/).  I tried his solution and played with swap, but the only change was that instead of the 4-5 lines of output there, the only output is now "Loading, please wait..."  I'm guessing its not swap related.

Ctrl+Alt+F2-F6 work great - those tty's spawn, and  can continue on normally from there.  I noticed that when I ran "ps a" that tty1 is NOT listed.

The only other additional piece of information is that during the latest update I ran, the "base-files" package was the only update for my system.  Doesn't appear that it would do anything of harm, but I'm not certain.

For what it's worth, here is my "/etc/event.d/tty1" file:
```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1
```Does anyone have any thoughts as to how I can get tty1 to spawn again 'as normal' at the end of the system startup process?

Thanks in advance.
-A

---

### Post by calverton on 2010-02-01
Lesson learned: if you start any programs in rc.local, make sure you include " > /dev/null 2>&1 &" or the equivalent needed for your situation ... :rolleyes:

---

