---
title: "Problem Uninstalling Midnight Commander"
date: 2009-10-31
forum: General Help
---

### Post by evfung on 2009-10-31
I'm currently using Linux Mint 7 and I posted this on their forums but couldn't seem to get any help so I'm trying a larger audience.


Basically I installed Midnight Commander but I got an error:

Setting up mc (2:4.6.2~git20080311-4ubuntu1) ...
update-alternatives: unable to make /usr/share/man/fr.UTF-8/man1/view.1.gz.dpkg-tmp a symlink to /etc/alternatives/view.fr.UTF-8.1.gz: No such file or directory
dpkg: error processing mc (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mc
E: Sub-process /usr/bin/dpkg returned an error code (1)


Checking Synaptic, it says its installed and when I try to uninstall it, i get this error:

Removing mc ...
update-alternatives: unable to make /usr/share/man/pl.ISO8859-2/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.pl.ISO8859-2.1.gz: No such file or directory
dpkg: error processing mc (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 mc
E: Sub-process /usr/bin/dpkg returned an error code (1)


And Synaptic still says its installed. Does anyone have any ideas on how to remove it.
Anytime I install or remove any other programs, the same error for MC keeps showing up, and its preventing me from doing other installations because dpkg keeps returning an error code.

---

