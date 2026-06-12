---
title: "get detailed list of installed packages"
date: 2010-11-24
forum: General Help
---

### Post by bowens44 on 2010-11-24
I know I can do a dpkg --get-selections to get a list of installed packages. 

Is there a way to get the version of the package listed as well?

Thanks

---

### Post by oldfred on 2010-11-24
these have more info.

List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

Alternative way with aptitude:
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
sudo xargs aptitude --schedule-only install < my-packages 

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/ch02s03s05.html")
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

