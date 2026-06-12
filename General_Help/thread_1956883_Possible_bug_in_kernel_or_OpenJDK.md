---
title: "Possible bug in kernel or OpenJDK?"
date: 2012-04-11
forum: General Help
---

### Post by Hotshot5000 on 2012-04-11
I have written a java server that listens on port 30003. Basically I have a selector.select() that waits until a connection is made and then services responses using interestOps(). I find it very interesting that after I launch a server and it waits in selector.select() for about 2 days (no connections made, no one is using the server) I lose the ability to connect to google.com or anything related to it such as youtube.com. It happens always: I start the server and after 2 days any connection to google with firefox, chromium, opera, lynx, wget anything doesn't work. After I kill the server and wait for about 12 hours the connection to google becomes possible again. I start the server and after 2 days the problem shows up. I don't use the server for a week, no problems. I keep the server for weeks on windows xp again no problems.. So I don't think it's my code but either OpenJdk or possible bad interaction between the jvm and networking subsystem in kernel.

For more information see [http://ubuntuforums.org/showthread.php?t=1954064](http://ubuntuforums.org/showthread.php?t=1954064)

I considered that this might be more than a netwrok problem so I posted in the general thread maybe somebody has an idea.

---

