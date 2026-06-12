---
title: "How to find out from cmdline if a certain software is installed?"
date: 2010-01-27
forum: General Help
---

### Post by pstein on 2010-01-27
I would like to find out from cmdline (!) if a certain software is already installed.
In redhat based Linuxes I could enter something like
 
rpm -qa|grep -i mysoftware
 
but this does not work in Ubuntu.
 
How can I find this out with apt?
 
What, if the installation was done by a perl script .pl rather than with apt.
 
How can I find out in this case?
 
Peter

---

### Post by The Men on 2010-01-27
```
dpkg -l | grep <keyword>

``````
dainis@ubuntu:~$ dpkg -l | grep glade
[COLOR=SeaGreen]**ii**[/COLOR]  glade                                 3.6.7-1ubuntu1                             GTK+ 2 User Interface Builder
**[COLOR=SeaGreen]ii[/COLOR] ** libglade2-0                           1:2.6.4-1                                  library to load .glade files at runtime
**[COLOR=SeaGreen]ii[/COLOR]  **libglade2-dev                         1:2.6.4-1                                  development files for libglade
**[COLOR=SeaGreen]ii[/COLOR]  **libglade2-ruby                        0.19.0-2ubuntu4                            Libglade 2 bindings for the Ruby language
**[COLOR=SeaGreen]ii[/COLOR]**  libglade2-ruby1.8                     0.19.0-2ubuntu4                            Libglade 2 bindings for the Ruby language
**[COLOR=SeaGreen]ii[/COLOR]**  libglade2.0-cil                       2.12.9-1                                   CLI binding for the Glade libraries 2.6
**[COLOR=SeaGreen]ii[/COLOR]**  libgladeui-1-9                        3.6.7-1ubuntu1                             GTK+ User Interface Build core library
**[COLOR=SeaGreen]ii[/COLOR]**  python-glade2                         2.16.0-0ubuntu1                            GTK+ bindings: Glade support
```

If the output is empty, no such software is present on your computer.

---

