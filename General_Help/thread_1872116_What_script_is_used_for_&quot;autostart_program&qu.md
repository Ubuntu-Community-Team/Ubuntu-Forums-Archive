---
title: "What script is used for &quot;autostart program&quot; option?"
date: 2011-10-30
forum: General Help
---

### Post by Hawkoon on 2011-10-30
I am using irecex program to control my multimedia apps with an remote control, and I had a hard time getting irexec to work after login.

I tried calling it from rc.local, I called it from an startup script under init.d and I tried calling it from .bash_login in my home dir, (I have no .bash_profile there). In the first two cases irexec was running after login (process ID was around 1530 each time), but it didn't process the remote control commands - only after killing and restarting it manually. Calling it from bash_login didn't do anything, the process wasn't even running after login then (perhaps due to some mistake on my end).

Anyway, in the end I added irexec to the autostart programs via System/Settings... and it is working perfectly now. Process ID is larger now, around 1700, and I wonder at what point in the booting and login sequence autostart programs are called, and what scripts are used for that?

Tanks for any advice.

~H

---

