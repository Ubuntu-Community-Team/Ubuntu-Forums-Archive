---
title: "How to reset system to proper version?"
date: 2012-04-07
forum: General Help
---

### Post by wired99 on 2012-04-07
I'm using Ubuntu 11.10 but I did install other desktops for a while to try them out.
I uninstalled them after getting conflicts with the ubuntu-software-center.

I'm still having difficulties with it, I cannot open it nor view the software-sources, it simply closes immediately after launch.

My system thinks that it is Linux Mint 12.
the command **lsb_release -a** returns with Linux Mint 12

How can I reset it so it to it's proper setting (which is Ubuntu 11.10)?

---

### Post by Cheesemill on 2012-04-07
The information is stored in /etc/lsb-release
For 11.10 it should read:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
```

---

### Post by wired99 on 2012-04-07
Thank you very much!!! :p

Everything is back to normal now (at least I think it is)
Programs are responding the way I think they should, so I really appreciate your help.

---

