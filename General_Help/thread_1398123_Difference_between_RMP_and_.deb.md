---
title: "Difference between RMP and .deb?"
date: 2010-02-04
forum: General Help
---

### Post by mahela007 on 2010-02-04
What's the difference between the RPM and .deb packages used on various linux distros?

---

### Post by s.fox on 2010-02-04
Hello,

RPM and Deb are both package management formats. They function in a very  similar way and the choice between the two is made by your distribution  generally. The packages let the system know what they contain, where it  should be put, what is required by the application and sometimes a  configuration script.
 
Tarballs like tar.gz are often source files from which you can build the  application. Sometimes they are a precompiled binaries that you can run  or install manually. While it is good to know how to work with source or  static binaries it's not the best way to keep a clean running system in  today's modern distro. A tar.gz or tar.bz2 is similar to a zip file.
 
Slackware however does include it's packages in a gzipped format that is  a more basic package manager. 
 
On the package front it's worth noticing that they are often combined  with systems to extend their usefulness. Rpm is often combined with  urpmi (Mandriva), yum (Red Hat, Fedora, Yellow Dog), yast (SUSE),  apt-get (Debian) or similar. These allow management of repositories and  automatic downloading of applications and dependencies.

-Silver Fox

---

