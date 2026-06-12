---
title: "broken dependencies for lilypond"
date: 2006-05-04
forum: General Help
---

### Post by [censored] on 2006-05-04
Hi. Been trying to install lilypond, the midi audio package.

Unfortunately, it doesn't want to install, gives this error:

> 
(Reading database ... 130517 files and directories currently installed.)
Unpacking lilypond (from .../lilypond_2.6.3-9~breezy1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 19: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 


obviously, it wants an executable called "/usr/bin/kpsewhich", which according to apt-file is part of the tetex-bin package. But if I try to install that package I get this error:

> 
sudo apt-get install tetex-bin
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  songwrite: Depends: lilypond but it is not going to be installed
  tetex-bin: Depends: libt1-5 (>= 5.0.2) but it is not going to be installed
             Depends: libwww-ssl0 (>= 5.4.0) but it is not going to be installed             Depends: tetex-base but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


What should I do?

---

### Post by jazzgossen on 2006-05-04
Either install the packages via synaptic, or try to install the packages listed as unmet dependencies manually:

apt-get install  libt1-5 libwww-ssl0  tetex-base

---

### Post by [censored] on 2006-05-05
jazzgossen just tried that. This was the result ......

> 
$ sudo apt-get install libt1-5 libwww-ssl0 tetex-base
Password:
onSorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  songwrite: Depends: lilypond but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


---

### Post by jazzgossen on 2006-05-05
Then I would try to run 'apt-get -f install' as the error message says. 

Is it the same if you try to install it using synaptic, too?

---

### Post by [censored] on 2006-05-05
All fixed. See this message 

[http://ubuntuforums.org/showthread.php?p=985368#post985368](http://ubuntuforums.org/showthread.php?p=985368#post985368)

See my last reply for details as to how I fixed it. There's a flaw in one of the packages in the repositories that totally screws apt-get.

---

