---
title: "museekd problems"
date: 2011-04-18
forum: General Help
---

### Post by skralljt on 2011-04-18
Hey, strange problem with museekd on an amd64 xubuntu install.  I can't seem to start or stop museekd.  When I try to start it, terminal responds that it is already running.  If I try to kill it, the terminal responds that no process is found.  If I search for it using htop, there is no result.  Does anybody have any idea what is going on with the version of museekd in the repos?
```
bjorn@amd64:~$ museekd restart
Museekd already running!
bjorn@amd64:~$ killall museekd
museekd: no process found
bjorn@amd64:~$ sudo killall museekd
museekd: no process found
bjorn@amd64:~$ museekd
Museekd already running!
bjorn@amd64:~$ killall Museekd
Museekd: no process found
bjorn@amd64:~$ sudo killall Museekd
Museekd: no process found
bjorn@amd64:~$ 

```

The only reason I am using this is because nicotine doesn't seem to work with the house router very well, even though soulseek works fine.

---

### Post by neyfrota on 2012-09-09
i try to start museekd as my non-root user

[FONT="Courier New"]$ museekd -h
Museekd already running!
$ museekd --help
Museekd already running!
$ museekd -h
Museekd already running!
$ museekd[/FONT]

He does not accept even help... mmmm.. lets switch to root and investigate. 

[FONT="Courier New"]root@ubuntu:/# ls /tmp/
hsperfdata_root  museekd.lock  pulse-PKdhtXMmr18n  subsonic[/FONT]

mmmm... museekd.lock... so lets delete

[FONT="Courier New"]root@ubuntu:/# rm /tmp/museekd.lock [/FONT]

and try start again as my non-root user

[FONT="Courier New"]$ museekd
[newnet.net.debug] 4096 file descriptors available for museekd.
[museekd.peers.warn] No valid client bind port set (range: 0 - 0).
[museekd.config.debug] Loading configuration '/darknet/.museekd/config.xml'.
[museekd.peers.warn] No valid client bind port set (range: 2234 - 0).
[museekd.peers.debug] Trying to bind to port 2234...
............[/FONT]

Bingo! :)

---

