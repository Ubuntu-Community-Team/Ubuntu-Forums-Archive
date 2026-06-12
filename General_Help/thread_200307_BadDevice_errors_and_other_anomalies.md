---
title: "BadDevice errors and other anomalies"
date: 2006-06-20
forum: General Help
---

### Post by Zeroangel on 2006-06-20
Hey all,

I've had Kubuntu running for probably about 14 total hours of actual computing time, have everything set-up, etc. But my machine is experiencing a few anomalies that are kind of annoying.

First of all, when I run a command like sudo kate filename I get a few errors```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-11666' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
ScimInputContextPlugin()
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()
```
While these errors don't prevent Kate from working, I have noticed anomalies on this machine, like spontaneous heavy reads from my HD which consume I/O and CPU cycles and slow the machine to a crawl, or errors when using BUMPS, that it can't open up the PTY (a type of terminal emulator backend, I think).

I got the errors when I first installed the machine (and I got the same errors on another machine I installed on, both use media keyboards and MS optical mice) so it might have something to do with my hardware, but I have no way of really telling.

Anyone have any ideas or speculation on where I might look?

---

### Post by Zeroangel on 2006-06-25
The BadDevice errors were caused by the Wacom drivers in xorg.conf, commenting them out solved it.

Thanks for nothing.

---

