---
title: "GUTTING a package from an Ubuntu install?"
date: 2010-07-16
forum: General Help
---

### Post by Spike the Dingo on 2010-07-16
I'm plagued by [this bug]("https://bugs.launchpad.net/ubuntu/+source/auctex/+bug/591092"). This latex package is kinda' mission critical and I can't uninstall/purge it without getting:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-chardet python-utidylib python-feedparser libtidy-0.99-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  preview-latex-style*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 291kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 263456 files and directories currently installed.)
Removing preview-latex-style ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing preview-latex-style (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 preview-latex-style
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What do I need to do to completely remove this package from my system? I'm not just talking about removing the files that come with
```
dpkg -L preview-latex-style
```
That's not the issue. I want to manually remove the package.

Can you guys help me? Thanks!

---

