---
title: "Broken .deb package"
date: 2006-05-04
forum: General Help
---

### Post by Circleback on 2006-05-04
Hi. I cant seem to get rid of a broken deb package. It is preventing me from installing some updates. Here is the message I get when I try to install any package:

Preparing to replace tangerine-icon-theme 0.10-0ubuntu1 (using .../tangerine-icon-theme_0.10-0ubuntu1_all.deb) ...
 Unpacking replacement tangerine-icon-theme ...
 touch: missing file operand
 Try `touch --help' for more information.
 dpkg: warning - old post-removal script returned error exit status 1
 dpkg - trying script from the new package instead ...
 touch: missing file operand
 Try `touch --help' for more information.
 dpkg: error processing /var/cache/apt/archives/tangerine-icon-theme_0.10-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
 touch: missing file operand
 Try `touch --help' for more information.
 dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
 Errors were encountered while processing:
 /var/cache/apt/archives/tangerine-icon-theme_0.10-0ubuntu1_all.deb
 E: Sub-process /usr/bin/dpkg returned an error code (1)


I've tried apt-get --fix-broken install, apt-get -f install, apt-get install -f, and aptitude. I always get the same message.

---

### Post by Sef on 2006-05-04
Try using Adept to fix it. 

Then Edit > fix broken packages

---

### Post by Al3xanR0 on 2006-05-04
[QUOTE=Circleback]Hi. I cant seem to get rid of a broken deb package. It is preventing me from installing some updates. Here is the message I get when I try to install any package:

Preparing to replace tangerine-icon-theme 0.10-0ubuntu1 (using .../tangerine-icon-theme_0.10-0ubuntu1_all.deb) ...
 Unpacking replacement tangerine-icon-theme ...
 touch: missing file operand
 Try `touch --help' for more information.
 dpkg: warning - old post-removal script returned error exit status 1
 dpkg - trying script from the new package instead ...
 touch: missing file operand
 Try `touch --help' for more information.
 dpkg: error processing /var/cache/apt/archives/tangerine-icon-theme_0.10-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
 touch: missing file operand
 Try `touch --help' for more information.
 dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
 Errors were encountered while processing:
 /var/cache/apt/archives/tangerine-icon-theme_0.10-0ubuntu1_all.deb
 E: Sub-process /usr/bin/dpkg returned an error code (1)


I've tried apt-get --fix-broken install, apt-get -f install, apt-get install -f, and aptitude. I always get the same message.[/QUOTE]


I had a similar issue because I was mixing Ubuntu and Debian repos.  The "--fix-broken option would have removed 285 packages in cluding essential ones, needless to say those didn't work for me either. Fortunately for me I remembered what the package I installed last, and I used Synaptic to resolve my issue. I selected the suspect broken package-> clicked package button-> clicked force version --which caused it to regress to the previous version.

---

### Post by Circleback on 2006-05-05
It fixed itself somehow

---

### Post by Al3xanR0 on 2006-05-05
[QUOTE=Circleback]It fixed itself somehow[/QUOTE]

That works too.:D

---

