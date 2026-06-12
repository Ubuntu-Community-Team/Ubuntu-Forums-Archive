---
title: "Hardware Abstraction Layer Hangs on boot"
date: 2006-06-04
forum: General Help
---

### Post by bockman on 2006-06-04
Upgraded to Dapper from Breezy yesterday, worked fine. Now, when my boot process gets to starting the hald, it hangs, and it'll never start. Even if I start it from the recovery command line, it won't fork ever. How do I fix this?

---

### Post by tkiesel on 2006-06-05
I've got the same problem. Came home from vacation two days ago, happily dist-upgraded my Dapper Beta to DApper Final, and couldn't reboot.  *chuckling*

I've been just doing Ctrl+Alt+F1 then Ctrl+Alt+F8 to clear the Usplash away from the boot scroll, and Ctrl+C when I see hald try to start up.  It's all I've found to get my machine bootable right now. I presume a bugfix will be inbound relatively quickly. :)

---

### Post by j0rd on 2006-06-07
same issue. Going to try and fix it now. Post here if you find a solution please.

---

### Post by j0rd on 2006-06-09
conflict between smb and hald. Resolve issue here.
[http://www.ubuntuforums.org/showthread.php?p=1118363&posted=1#post1118363](http://www.ubuntuforums.org/showthread.php?p=1118363&posted=1#post1118363)

Maybe this thread too, i didn't read it.
[http://www.ubuntuforums.org/showthread.php?t=192025&highlight=hald](http://www.ubuntuforums.org/showthread.php?t=192025&highlight=hald)

---

