---
title: "Ubuntu 10.10 will not shutdown - maybe wine related"
date: 2010-10-29
forum: General Help
---

### Post by thedemon13666 on 2010-10-29
Hi

I am currently running Ubuntu 10.10 on my Maxdata ECO4700IW laptop.  Everything works great except after I have started utorrent the laptop freezes on the shutdown splash screen.  A couple of the dots turn on and then it freezes there.  Rebooting works fine however.

I have already tried killing utorrent and wine at the command line using

killall -9 uTorrent.exe
killall wineserver
winserver -k

I was using wine 1.0.2 but downgraded to 1.0.1 however still had the same problem.

Thanks for the help

xx

---

### Post by thedemon13666 on 2010-10-31
bump anyone?

---

### Post by Vigh on 2010-10-31
utorrent has issues with linux, just use a native linux bit-torrent client, also the latest stable version of wine is 1.2, hope this helps a bit, regards

---

### Post by thedemon13666 on 2010-10-31
I can't really use a native one (private trackers etc).  I have also tried wine 1.2 but still there seems to be a shutdown freeze problem..

---

### Post by Vigh on 2010-10-31
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)

try following this guide, read what other people have to say, seems they have managed to get utorrent working okay, the latest unstable version is platnum standard, which means it works on wine

---

