---
title: "problems after ldconfig"
date: 2010-11-03
forum: General Help
---

### Post by JunCTionS on 2010-11-03
Hello,
yesterday I tried adding a directory to the library path considering [this thread]("http://ubuntuforums.org/showthread.php?t=1498755").

After running "ldconfig -v" it still didn't seem to work.

After rebooting no graphic session was available so I had to run in recovery mode and reconfigure the graphics.

Then I had no title bars on the windows or Alt+Tab funtionality, which was fixed by turning off effects. Now if I try to turn them back on it looks for drivers and then says it can't turn them on.

And adobe flash doesn't have any audio, so I'm guessing I'm running with a slightly messed up library path.

Does anyone know how to further diagnose/fix this?

In /var/log/messages I'm also getting some error messages that were not there before the ldconfig:

> 
[   19.964073] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   21.285640] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro


but I'm guessing all of this will be fixed whenever I restore the library path.

(As can be infered from above I'm running Ubuntu 10.10 on 64bit and have double boot)

---

### Post by JunCTionS on 2010-11-04
*bump* and update
flash works sometimes and now rhythmbox opens but doesn't play (hitting play does nothing).
I'm thinking of doing a clean install, but that would make me have to recompile/install several packages and that takes time.
anyone care to help?

When running rhythmbox from terminal I get this error:
> (rhythmbox:3263): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

So following [this thread]("http://ubuntuforums.org/showthread.php?t=1592270")  with a similar issue I uninstalled rhythmbox-ubuntuone-music-store. but I still get the same error.

Anyone?

---

