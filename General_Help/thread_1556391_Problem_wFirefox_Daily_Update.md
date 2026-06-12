---
title: "Problem w/Firefox Daily Update"
date: 2010-08-19
forum: General Help
---

### Post by tomasGM on 2010-08-19
Hi; long time no post.  I am having a problem with the daily Firefox build from [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) repository.

This morning I ran Update Manager and got the newest Chromium and Firefox builds.  Downloaded and installed, mostly.  The Firefox install hung forever on the:

Setting up firefox (3.6.9~hg20100817r34537+nobinonly-0ubuntu1~umd2~lucid) ...

Step and I had to shutdown to go to work.

Ran - sudo dpkg --configure -a and am now in the 15th minute of waiting.

Any suggestions???????

---

### Post by xangua on 2010-08-19
remove the PPA and use the stable version

---

### Post by tomasGM on 2010-08-19
> **xangua said:**
> remove the PPA and use the stable version

I did remove the ppa and it actually looks like the newest daily build IS installed but dpkg is convince that it hasn't finished setting up the package.

As a result every time is install or update dpkg decides to finish the setup and hangs on the Firefox step.

After a reboot I can get into Synaptic and the Firefox package shows up in the installed packages and nothing is list as a broken package.

---

### Post by TheAxeR on 2010-08-19
I have the same exact issue.  Any idea if this will inhibit other updates?

---

### Post by adben on 2010-08-19
Try,
```
sudo dpkg -P --force-all firefox
```
should work

---

### Post by tomasGM on 2010-08-19
> **adben said:**
> Try,
```
sudo dpkg -P --force-all firefox
```
should work

Used this and it works.  It purges Firefox and I had to reinstall but do not have the error anymore.

Thx.

---

### Post by xangua on 2010-08-19
easier next time: use "ppa-purge" to remove the ppa and also rollback to the default packages incluided in lucid/current repository

forgot to mention that :P

---

### Post by TheAxeR on 2010-08-20
I just want to add my thanks as well.

---

### Post by soryu on 2010-08-20
this also worked for me. thanks

 anyone know what happened?

should i go ahead and do the PPA-PURGE?

---

### Post by tomhung on 2010-08-25
I had to kill all the lock files
```

sudo rm -rf /var/lib/dpkg/lock
sudo rm -rf /var/cache/apt/archives/lock

```

then purge firefox
```
sudo dpkg -P --force-all firefox
```

then update apt
```
sudo apt-get update
```

then 
```
sudo apt-get install -f
```

---

