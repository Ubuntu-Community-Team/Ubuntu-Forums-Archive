---
title: "dpkg errors"
date: 2010-12-01
forum: General Help
---

### Post by HalfEmptyHero on 2010-12-01
Whenever I try to install or remove a program, I get the following error
```
dpkg: warning: files list file for package `libavahi-common-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxres1' missing, assuming package has no files currently installed.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'ubuntu-mono' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by dino99 on 2010-12-01
reboot

sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by HalfEmptyHero on 2010-12-01
Tried that, but I still get the error.

---

### Post by gmargo on 2010-12-01
Clearly you have some corrupted files in your /var/lib/dpkg/info/ directory.  If those are the only errors you receive it may be fixable.

Before you do anything else, create a backup copy of the /var/lib/dpkg/info/ directory.

Then remove the corrupted ubuntu-mono.list file.  Then reinstall the four affected packages.

```

sudo cp -pr /var/lib/dpkg/info /var/lib/dpkg/info.backup
sudo rm /var/lib/dpkg/info/ubuntu-mono.list
sudo aptitude -V reinstall ubuntu-mono
sudo aptitude -V reinstall libavahi-common-data
sudo aptitude -V reinstall libgtk2.0-common
sudo aptitude -V reinstall libxres1

```

You might take a look at the content of the corrupted ubuntu-mono.list file; it might give you a clue as to what caused the problem.

---

### Post by HalfEmptyHero on 2010-12-01
That did it, thanks.

---

