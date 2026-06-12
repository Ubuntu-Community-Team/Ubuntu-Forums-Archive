---
title: "Dangers of remapping /bin/sh"
date: 2009-09-14
forum: General Help
---

### Post by doloctona on 2009-09-14
Hey all,

So, I've finally got my system up and running using dmraid to make the software-raid work properly, and building 9.04 up mostly from the command-line (the installer barfs when I try to install with / mapped to /dev/mapper/isw_ceeaabjdha_store1).  The point is, the install has taken a while and I don't now want to break the system, much as I enjoy fresh installs.

Anyway, I'm trying to get some custom shell scripts to work (these are shared scripts at the place I work, so I cannot change them without breaking others build environments).  Unfortunately, they are expecting to be run using ksh, and /bin/sh maps to dash.

I guess my question is, if I remap /bin/sh to /bin/ksh, am I going to break stuff?  e.g. make the system unbootable (that would be the worst outcome - I'm sure I could recover using the live-cd, but still a scary prospect)?

Thanks in advance,

James

---

### Post by doloctona on 2009-09-15
Well, I managed to reboot with /bin/sh pointing at /bin/ksh by mistake.  The short answer is, there are a lot of warning messages (/etc/rc.d/xxx: local: file not found or something along those lines) which look nasty (sudo apt-get install usplash helps!), but it does boot.

---

### Post by aesis05401 on 2009-09-15
If your scripts are declaring the shell on the sha-bang line you should only need to have ksh present in one of the directories specified in the PATH environment variable... Unless I am missing something.  

Does this make sense?

---

### Post by Bachstelze on 2009-09-15
What do your scripts have in the first line? it should start with #!.

---

### Post by doloctona on 2009-09-15
It's not an issue with finding ksh, it's an issue that the scripts (which are written for QNX, to be honest) expect /bin/sh to point to /bin/ksh, and in my case /bin/sh points to /bin/dash.

It would be nice to change the scripts to #!/bin/ksh, but that would break things for other people.

---

### Post by Bachstelze on 2009-09-15
Then just make /bin/sh point to /bin/ksh. ksh is POSIX-compliant, so it shouldn't mess up your Ubuntu.

---

### Post by aesis05401 on 2009-09-15
For longterm it would be good if all your group's scripts explicitly declared the shell...  That being said, you are not alone in the boat of having legacy scripts pointing to /bin/sh ;)

---

