---
title: "how to remove  lilypond-data?"
date: 2006-02-17
forum: General Help
---

### Post by shams2 on 2006-02-17
hi,
this package prevent ap-get and aptitude to install or upgarde any package, the error is:
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack! Something bad happened while installing packages. Trying to recover

i did:
dpkg -s  lilypond-data
Package: lilypond-data
Status: deinstall ok half-installed
Priority: optional
Section: tex
Installed-Size: 15064
pleas help me how to remove this package?

---

### Post by Greg2 on 2006-02-17
[QUOTE=shams2]hi,
this package prevent ap-get and aptitude to install or upgarde any package, the error is:
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
lilypond-data
[/QUOTE]The solution is in this thread:
[http://ubuntuforums.org/showthread.php?t=111991&page=2](http://ubuntuforums.org/showthread.php?t=111991&page=2)
Please read, starting with my first post on page two.

---

### Post by shams2 on 2006-02-17
thanks for reply i run the apt-get install -f and this was the output:
#apt-get install -f
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  lilypond-data
0 upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 103302 files and directories currently installed.)
Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

in the synaptic the package was marked for the complete removal, when i clicked in the apply to remove the package,  got the above error.
subprocess post-removal script returned error exit status 1

---

### Post by Greg2 on 2006-02-17
Please read the rest of that thread.

---

### Post by shams2 on 2006-02-17
thanks so much the next  trick worked.

---

