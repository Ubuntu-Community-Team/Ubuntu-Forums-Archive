---
title: "shell login annoyance."
date: 2010-05-21
forum: General Help
---

### Post by ds5v50 on 2010-05-21
At login using ssh I get the annoying message that there are 520 packages to be updated. I have searched and have had no luck. The system is updated with the latest. The kicker is that when there are packages available, It tells you before the note showing 520 packages.

    If someone would point me in the right direction to resolve this it would be greatly appreciated.

```

GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

520 packages can be updated.
0 updates are security updates.

Checking for a new ubuntu release
No new release found
Last login: Fri May 21 08:24:07 2010 from station2.tatorz.com

```

---

### Post by gmargo on 2010-05-21
Most likely /etc/motd.tail.

See this thread: [http://swiss.ubuntuforums.org/showthread.php?p=9142161](http://swiss.ubuntuforums.org/showthread.php?p=9142161)

---

### Post by ds5v50 on 2010-05-23
Looks like I really need to brush up on my searching. That was it thank you.

Brian

---

