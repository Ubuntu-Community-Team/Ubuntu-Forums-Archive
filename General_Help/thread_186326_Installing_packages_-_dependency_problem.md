---
title: "Installing packages - dependency problem"
date: 2006-06-01
forum: General Help
---

### Post by blackjack6.21.91 on 2006-06-01
I was trying to install a debian package not available in the repos (wired), which requires a dependency **libsndfile1**.  When I double click my installer, it says dependency libsndfile1 is not satisfiable.  Synaptic says it's installed.  Whats the problem?

---

### Post by Rackerz on 2006-06-01
Try installing using the Terminal.

---

### Post by thero on 2006-06-01
i have no idea but do you have libsndfile1-dev?

---

### Post by blackjack6.21.91 on 2006-06-01
I installed libsndfile1-dev and tried installing using the terminal.  No luck.  Heres my session


sudo dpkg -i /home/bloaner/Desktop/docs/installations/wired_0.2-1_i386.deb
Password:
dpkg: status database area is locked by another process
bloaner@bloaner-laptop:~/Desktop/docs/installations$ sudo dpkg -i /home/bloaner/Desktop/docs/installations/wired_0.2-1_i386.deb
Selecting previously deselected package wired.
(Reading database ... 98437 files and directories currently installed.)
Unpacking wired (from .../wired_0.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of wired:
 wired depends on libsndfile1 (>= 1.0.14); however:
  Version of libsndfile1 on system is 1.0.12-3.
 wired depends on libsamplerate0 (>= 0.1.2); however:
  Package libsamplerate0 is not installed.
 wired depends on libsoundtouch1c2 (>= 1.3.0); however:
  Package libsoundtouch1c2 is not installed.
dpkg: error processing wired (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wired

---

### Post by gatekeep on 2006-06-01
>  wired depends on libsndfile1 (>= 1.0.14); however:
  Version of libsndfile1 on system is 1.0.12-3.


you have the wrong version of libsndfile1 ... your's is 1.0.12-3 you need something greater then 1.0.14

---

### Post by blackjack6.21.91 on 2006-06-01
ok, your right, my version was outdated.  so i went to the libsndfile website to compile from source but now i'm getting errors.

when i ran ./configure the only problem seemed this

Compiling some other packages against libsndfile may require
the addition of "/usr/local/lib/pkgconfig" to the
PKG_CONFIG_PATH environment variable.

After that it didn't compile right.  I'm kinda a terminal newb so iono what the problem is.  Anyone know anything I can do?

---

### Post by gatekeep on 2006-06-01
You could try the Debian libsndfile1...[http://packages.debian.org/testing/libs/libsndfile1](http://packages.debian.org/testing/libs/libsndfile1) though I'm not sure it will work

---

### Post by blackjack6.21.91 on 2006-06-01
I don't know which link to pull from that page... newbish, huh??

If you could just give me the debian link for i386 architecture or tell me what to download that would be awesome.

---

### Post by blackjack6.21.91 on 2006-06-01
nevermind i got the download

---

