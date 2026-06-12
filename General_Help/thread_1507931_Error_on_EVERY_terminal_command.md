---
title: "Error on EVERY terminal command"
date: 2010-06-12
forum: General Help
---

### Post by Jake007g on 2010-06-12
Ok, so not long after I first installed Ubuntu, I installed gtk-recordmydesktop through apt-get. My system (Laptop) can't handle gtk-recordmydesktop very well, so I un-installed it through apt-get remove. Now, whatever I do in terminal, for instance installing other programs I get an error at the end of the output, even though what I was trying to do is successful. It doesn't really affect me at all, it just gets annoying. This is the error I get:

> Setting up gtk-recordmydesktop (0.3.8-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gtk-recordmydesktop (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gtk-recordmydesktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


If anyone knows how to fix this, please let me know.

thanks in advance.

-Jake

---

### Post by llawwehttam on 2010-06-12
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

---

