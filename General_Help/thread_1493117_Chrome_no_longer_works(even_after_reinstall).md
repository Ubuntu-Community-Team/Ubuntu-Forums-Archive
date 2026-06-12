---
title: "Chrome no longer works(even after reinstall)"
date: 2010-05-25
forum: General Help
---

### Post by NecroPsyChroNauTron on 2010-05-25
So things froze, and I had to hit the reset button.
I reboot, and try to launch chrome from it's shortcut icon...........nothing.

Upon launching from terminal I see this.

[3185:3194:9191183054:FATAL:base/shared_memory_posix.cc(193)] Creating shared memory in /dev/shm/com.google.chrome.G7CN8Y failed. This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 777 /dev/shm' to fix.: No such file or directory
Aborted


I tried the chmod as reccomended and see
chmod: changing permissions of `/dev/shm': Read-only file system

The folder is not taking permissions. Can I even take permission if owned by root? ( forgive me if this is a noob question)

Anyways, tried sudo apt-get install --reinstall google-chrome-beta and nothing.
What next? Purge it?

Any suggestions are very welcome.

---

### Post by NecroPsyChroNauTron on 2010-05-25
Being impatient I tried purge just to be sure, and can't seem to apt-get install now as the package is not found.
So binus newb question: Was I able to apt-get install --reinstall  before because I had downloaded the package previously?
Or did purging somehow remove the software source from my lists?

Note:  I did find this page and manually re-add the source. [http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

---

