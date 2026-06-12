---
title: "ENORMOUS .xsession-errors file"
date: 2011-11-16
forum: General Help
---

### Post by Ghostlove on 2011-11-16
We touched on this in my previous post [Not enough disk space](http://ubuntuforums.org/showthread.php?t=1865544) but even after the workarounds posted there, the problem has returned.

Within 24 hours my .xsession-errors file is reaching over 200GB. It's completely destroying my Ubuntu experience; Thunderbird's not working, Firefox is hanging, Amarok and Rhythmbox are refusing to do anything and every ten seconds or so the whole system freezes and takes a good thirty seconds to get going again.

I've just checked /etc/X11/Xsession and it does indeed have "ERRFILE=/dev/null" in it, which surely means that the errors should be being written to nowhere, effectively? So why is this still happening?

Please, please, can anyone help me? This was not happening before I upgraded to 11.10 (64-bit). I'm watching the file grow at astounding speed as we speak. :(

---

### Post by hwttdz on 2011-11-16
Just to get you a working platform until you iron this out, you can run 

```
while [[ 1 ]]; do rm ~/.xsession-errors; sleep 10; done
```

in a terminal, and just put the window out of the way.  That will delete the file every 10 seconds, so you don't run out of space.  This is an ugly hack and will actually make debugging harder... but having your machine lock up frequently also makes debugging harder...

Did you end and restart the x-session (probably by rebooting) after changing where you wanted x-session errors to go?

---

