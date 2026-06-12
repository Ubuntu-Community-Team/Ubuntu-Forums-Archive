---
title: "can't install and upgrade packages?"
date: 2006-02-16
forum: General Help
---

### Post by shams2 on 2006-02-16
hi,
when i want to install or upgrade packages, the apt-get and aptitude downloading the necessary packages, but while installation want to remove lilypond-data but then exiting  with this error message:
Preconfiguring packages ...
(Reading database ... 103302 files and directories currently installed.)
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data 
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
and no upgrade and nothing was installed, i tried to remove the  lilypond-data manually but with locate ilypond-data there is no output. please help me.

---

### Post by shams2 on 2006-02-17
hi,
please help me how to solve this problem?

---

