---
title: "lcdproc on remote server?"
date: 2012-08-09
forum: General Help
---

### Post by ejs75 on 2012-08-09
Hello,

Just did a new build with 12.04 Ubuntu & have lcdproc working nicely with my lcd display using the lis driver.

Now I am trying to get lcdproc to read info from my remote server running 10.04. I copied over LCDd (daemon), LCDd init script, lis.so driver, & LCDd.conf file. Configured when needs to be.

I cannot get lcdproc to work. When I run it on my machine using a modified lcdproc.conf to point to my remote server. Says:

```
Error connecting to LCD server **.***.***.** on port 13666.
Check to see that the server is running and operating normally.
```My IP address is edited out. The LCD server is running on the emote machine. I have tired using localhost ip and my server's ip in LCDd.conf with no success.

Anyone got this working remotely? Obviously I have missed something vital.

---

