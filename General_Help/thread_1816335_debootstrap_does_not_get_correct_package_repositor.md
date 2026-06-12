---
title: "debootstrap does not get correct package repository"
date: 2011-08-01
forum: General Help
---

### Post by RaverWild on 2011-08-01
I am trying to run "sudo pbuilder create" where it runs debootstrap. Then it says:

```
I: Checking component main on http://bg.archive.ubuntu.com/ubuntu...
```

Problem is that this is the old repo I've used. After installing pbuilder and the other dpkg essential packages I've run "sudo pbuilder create", noticed the message of the repo and since I am no longer in Bulgaria, interrupted the script, went to synaptic and changed the repo from there (now is [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/)). Even rebooted. Double-checked in synaptic the repo is still changed, grepped the files in /etc/apt for "bg" and all results were commented. I ran again "sudo pbuilder create" and it still reports the old repo. 

So where does debootstrap reads the repo setting from and how to fix it?

Thanks

---

### Post by sisco311 on 2011-08-02
debootstrap has no configuration file. pbuilder passes the mirror to debootstrap as an argument. pbuilder's system-wide configuration file is /etc/pbuilderrc and the personal configuration file is  ${HOME}/.pbuilderrc. You have to change the value of MIRRORSITE.

---

### Post by RaverWild on 2011-08-04
Thanks! Fixed it.

---

### Post by sisco311 on 2011-08-04
Cool! Don't forget to mark this thread as solved.

---

