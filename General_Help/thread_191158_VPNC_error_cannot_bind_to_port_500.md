---
title: "VPNC error: cannot bind to port 500"
date: 2006-06-07
forum: General Help
---

### Post by DarkStarDeity on 2006-06-07
I've just installed and configured KVpnc to connect to my work, and after fixing a minor hiccup with not finding the tun module, I'm now getting the following error:

"error: /usr/sbin/vpnc binding to port 500: permission denied"

What would be causing this? How can I find out what processes are using which ports? And if this port is already used by another process (it shouldn't be, the only service I have running here is samba), can I configure vpnc to use another port?

Also, KVpnc doesn't quit cleanly, I have to kill it from the system monitor. What could be causing this and how can I fix it?

---

### Post by DarkStarDeity on 2006-06-07
OK, after a bit deeper digging on the forums, I found [this thread]("http://ubuntuforums.org/showthread.php?t=80076") and applying the instructions from the second comment down (just using plain vpnc rather than KVpnc) I now have a VPN connection.

---

### Post by indramilo on 2006-06-11
you can fix this error by  making yourself admin with the sudo command, I fixed it with that

---

