---
title: "Post 9.10 Upgrade Issues"
date: 2009-11-24
forum: General Help
---

### Post by justinjw on 2009-11-24
I upgraded recently from 9.04 on my HP Mini, and I've been experiencing some annoying problems:

1)  I cannot open any programs from the Applications menu (or access anything in the Places menu).  When I click on something, it will say "opening xxxxx" at the bottom of the screen, and then nothing.  Programs that are in my favorites panel open without a problem.

2)  My computer takes a LONG TIME to start now.  In 9.04, I was at the login screen in about 30 seconds, and now it takes at least 2 minutes, plus 2 minutes post log-in.

3)  When I right click on my desktop, nothing happens (perhaps related to number 1)

4)  And this may not be related to the upgrade, but since the upgrade I've been having problems with Firefox 3.5.5.  Web pages take a long time to load (at least 10 times longer than they take in Opera), and the back & forward buttons are disabled.


Any help is greatly appreciated!

---

### Post by dcstar on 2009-11-24
> **justinjw said:**
> I upgraded recently from 9.04 on my HP Mini, and I've been experiencing some annoying problems:

1)  I cannot open any programs from the Applications menu (or access anything in the Places menu).  When I click on something, it will say "opening xxxxx" at the bottom of the screen, and then nothing.  Programs that are in my favorites panel open without a problem.

2)  My computer takes a LONG TIME to start now.  In 9.04, I was at the login screen in about 30 seconds, and now it takes at least 2 minutes, plus 2 minutes post log-in.

3)  When I right click on my desktop, nothing happens (perhaps related to number 1)

4)  And this may not be related to the upgrade, but since the upgrade I've been having problems with Firefox 3.5.5.  Web pages take a long time to load (at least 10 times longer than they take in Opera), and the back & forward buttons are disabled.


Any help is greatly appreciated!

Check your dns, network and system name settings:

```
cat /etc/hosts
cat /etc/hostname
cat /etc/resolv.conf
```

---

