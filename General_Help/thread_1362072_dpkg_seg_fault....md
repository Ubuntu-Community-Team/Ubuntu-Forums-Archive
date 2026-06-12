---
title: "dpkg seg fault..."
date: 2009-12-22
forum: General Help
---

### Post by dvlchd3 on 2009-12-22
So I've seen some other posts, and it seems none offer a good solution...

I ran an upgrade via apt-get today, and at the very end, I received a segmentation fault.  With the exception of apt-get clean and apt-get update, every other apt-get command ends in a seg fault error.

Per another thread, I ran dpkg-reconfigure -a, however, this did not resolve the issue.  Someone else suggested a restart, this did not fix it either.

I'm confused as to what actually happened, and not really sure what happened.

Example of command output:
```

dan@BRICKMAN:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault

```

Attached is the dpkg.log log file.

Any suggestions on how to resolve this issue?

---

### Post by dvlchd3 on 2009-12-23
Ok, it appears this was an issue with just apt-get.  Reinstalling it appears to have fixed the problem.

```

sudo aptitude reinstall apt

```

---

### Post by slotto on 2010-04-11
Thanks!

---

