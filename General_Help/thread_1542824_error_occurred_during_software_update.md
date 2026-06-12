---
title: "error occurred during software update"
date: 2010-07-31
forum: General Help
---

### Post by fethio on 2010-07-31
during the software update process, the git package could not be updated with the following error:

[INDENT]E: /var/cache/apt/archives/git_2%3a1.7.2.1-1~avh1~lucid1_i386.deb: trying to overwrite '/etc/emacs/site-start.d/50git-core.el', which is also in package git-core 2
[/INDENT]
How do I get around this problem? Restarting the update manager does not resolve the issue, I get the same error...

The messages from apt-get::

(Reading database ... 218552 files and directories currently installed.)
Unpacking git (from .../git_2%3a1.7.2.1-1~avh1~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/git_2%3a1.7.2.1-1~avh1~lucid1_i386.deb (--unpack):
 trying to overwrite '/etc/emacs/site-start.d/50git-core.el', which is also in package git-core 2:1.7.2.1-1~avh1~lucid1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/git_2%3a1.7.2.1-1~avh1~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of git-core:
 git-core depends on git (>> 2:1.7.0.2); however:
  Package git is not installed.
dpkg: error processing git-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 git-core

---

### Post by fethio on 2010-07-31
problem solved by:

apt-get remove git-core
apt-get install git-coreh

---

