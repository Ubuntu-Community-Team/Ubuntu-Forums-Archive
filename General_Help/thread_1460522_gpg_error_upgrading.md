---
title: "gpg error upgrading"
date: 2010-04-22
forum: General Help
---

### Post by tw11 on 2010-04-22
Sorry if this thread exists already. I tried searching for it but didn't really find one that fix my problem or at least one with a solution I understood.

A couple of days, all of a sudden update stopped working. I get the following result when doing sudo apt-get update
```
$ sudo apt-get update
Get:1 http://astromirror.uchicago.edu karmic Release.gpg [189B]
Ign http://astromirror.uchicago.edu karmic/main Translation-en_US
Ign http://astromirror.uchicago.edu karmic/restricted Translation-en_US
Ign http://astromirror.uchicago.edu karmic/universe Translation-en_US
Ign http://astromirror.uchicago.edu karmic/multiverse Translation-en_US
Get:2 http://astromirror.uchicago.edu karmic-updates Release.gpg [189B]
Ign http://astromirror.uchicago.edu karmic-updates/main Translation-en_US
Ign http://astromirror.uchicago.edu karmic-updates/restricted Translation-en_US
Ign http://astromirror.uchicago.edu karmic-updates/universe Translation-en_US
Ign http://astromirror.uchicago.edu karmic-updates/multiverse Translation-en_US
Get:3 http://astromirror.uchicago.edu karmic-security Release.gpg [189B]
Ign http://astromirror.uchicago.edu karmic-security/main Translation-en_US
Ign http://astromirror.uchicago.edu karmic-security/restricted Translation-en_US
Ign http://astromirror.uchicago.edu karmic-security/universe Translation-en_US
Ign http://astromirror.uchicago.edu karmic-security/multiverse Translation-en_US
Hit http://astromirror.uchicago.edu karmic Release
Hit http://astromirror.uchicago.edu karmic-updates Release
Hit http://astromirror.uchicago.edu karmic-security Release
Ign http://astromirror.uchicago.edu karmic Release
Ign http://astromirror.uchicago.edu karmic-updates Release
Hit http://astromirror.uchicago.edu karmic/main Packages
Ign http://astromirror.uchicago.edu karmic-security Release
Hit http://astromirror.uchicago.edu karmic/restricted Packages
Hit http://astromirror.uchicago.edu karmic/main Sources
Hit http://astromirror.uchicago.edu karmic/restricted Sources
Hit http://astromirror.uchicago.edu karmic/universe Packages
Hit http://astromirror.uchicago.edu karmic/universe Sources
Hit http://astromirror.uchicago.edu karmic/multiverse Packages
Hit http://astromirror.uchicago.edu karmic/multiverse Sources
Hit http://astromirror.uchicago.edu karmic-updates/main Packages
Hit http://astromirror.uchicago.edu karmic-updates/restricted Packages
Hit http://astromirror.uchicago.edu karmic-updates/main Sources
Hit http://astromirror.uchicago.edu karmic-updates/restricted Sources
Hit http://astromirror.uchicago.edu karmic-updates/universe Packages
Hit http://astromirror.uchicago.edu karmic-updates/universe Sources
Hit http://astromirror.uchicago.edu karmic-updates/multiverse Packages
Hit http://astromirror.uchicago.edu karmic-updates/multiverse Sources
Hit http://astromirror.uchicago.edu karmic-security/main Packages
Hit http://astromirror.uchicago.edu karmic-security/restricted Packages
Hit http://astromirror.uchicago.edu karmic-security/main Sources
Hit http://astromirror.uchicago.edu karmic-security/restricted Sources
Hit http://astromirror.uchicago.edu karmic-security/universe Packages
Hit http://astromirror.uchicago.edu karmic-security/universe Sources
Hit http://astromirror.uchicago.edu karmic-security/multiverse Packages
Hit http://astromirror.uchicago.edu karmic-security/multiverse Sources
Fetched 567B in 0s (10.1kB/s)
Reading package lists... Done
W: GPG error: http://astromirror.uchicago.edu karmic Release: Unknown error executing gpgv
W: GPG error: http://astromirror.uchicago.edu karmic-updates Release: Unknown error executing gpgv
W: GPG error: http://astromirror.uchicago.edu karmic-security Release: Unknown error executing gpgv

```So it seems the problem is with libreadline.so.6 and I would have removed it but it seems as if it has alot of dependencies and I don't want to mess up my computer.

Thanks for any help.

EDIT: also, this happens with any software repository, not just the uchicago one

---

### Post by tw11 on 2010-04-23
bump. anyone?

---

### Post by tw11 on 2010-04-23
bumppppp

---

### Post by jfleming9232 on 2010-05-14
I get a similar message when trying to get gpg keys:

gpg: error while loading shared libraries: libreadline.so.6: cannot open shared object file: No such file or directory

Any suggestions?

I just upgraded to Lucid and I'm running a Dell inspiron 1525 if that helps.

---

