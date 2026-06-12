---
title: "can't install programs through software center"
date: 2012-05-22
forum: General Help
---

### Post by wjsomething on 2012-05-22
Whenever I try to install a program through the software center the installation gets about halfway and then I get the following error message:

```
installArchives() failed: Selecting previously unselected package libaacs0.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libgstreamer0.10-0' is missing final newline
Error in function:
 SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
```

Also,since this may be related, the movie player that's already installed (the default I guess) doesn't open at all.

Any advice is appreciated, thanks.

---

### Post by MadmanRB on 2012-05-22
try a terminal, located under "accesories" in your menu
and put in this:

```
sudo apt-get update
```

and see if it spits out errors again.
Sometimes apt (the thing used to get packages in ubuntu) gets stuck, I had similar issues myself in the past

---

### Post by wjsomething on 2012-05-23
I tried that and it went through whatever process that started just fine, but I still can't install anything and I get the same set of errors.

---

