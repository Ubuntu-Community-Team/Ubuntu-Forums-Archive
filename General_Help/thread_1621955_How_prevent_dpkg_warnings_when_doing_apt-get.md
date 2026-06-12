---
title: "How prevent dpkg warnings when doing apt-get?"
date: 2010-11-14
forum: General Help
---

### Post by watchpocket on 2010-11-14
Every time I run "apt-get" or "apt-get autoremove" terminal-commands lately, I see this:

```


Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `mythtv-theme-metallurgy' missing, assuming package has no files currently installed.
(Reading database ... 10%
dpkg: warning: files list file for package `mythtv-theme-graphite' missing, assuming package has no files currently installed.
(Reading database ... 25%
dpkg: warning: files list file for package `mythtv-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mythtv-theme-retro-osd' missing, assuming package has no files currently installed.
(Reading database ... 40%
dpkg: warning: files list file for package `mythtv-theme-mono-osd' missing, assuming package has no files currently installed.
(Reading database ... 55%
dpkg: warning: files list file for package `mythtv-status' missing, assuming package has no files currently installed.
(Reading database ... 60%
dpkg: warning: files list file for package `mythtv-common' missing, assuming package has no files currently installed.
(Reading database ... 65%
dpkg: warning: files list file for package `mythtv-theme-iulius-osd' missing, assuming package has no files currently installed.
(Reading database ... 70%
dpkg: warning: files list file for package `mythtv-theme-blueosd' missing, assuming package has no files currently installed.
(Reading database ... 80%
dpkg: warning: files list file for package `mythtv-theme-mythbuntu' missing, assuming package has no files currently installed.
(Reading database ... 95%
dpkg: warning: files list file for package `mythtv-theme-titivillus-osd' missing, assuming package has no files currently installed.
(Reading database ... 278071 files and directories currently installed.)


```At one point I did remove some mythtv stuff piecemeal after I thought I'd previously  removed all things mythtv.  Anyone know what I need to do?

---

### Post by 73ckn797 on 2010-11-14
Try ```
sudo apt-get purge
```and the program name.

---

