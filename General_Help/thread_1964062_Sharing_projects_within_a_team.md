---
title: "Sharing projects within a team?"
date: 2012-04-23
forum: General Help
---

### Post by robertahilljr on 2012-04-23
Hi, can anyone tell me, what would be the best way to share a project between a team? Obviously Canonical are doing it some how but I am unsure how to achieve this. I am currently building a distro, now though I have other team member O can't see the best way to share it between them. 

If its any help, the distro is being built under virtualbox, although is there any better way to work on this?

Kind regards,

Rob

---

### Post by techsupport on 2012-04-23
> **robertahilljr said:**
> Hi, can anyone tell me, what would be the best way to share a project between a team? Obviously Canonical are doing it some how but I am unsure how to achieve this. I am currently building a distro, now though I have other team member O can't see the best way to share it between them. 

If its any help, the distro is being built under virtualbox, although is there any better way to work on this?

Kind regards,

Rob

This is what I use:

OpenProj is an open source project management software intended as a  complete desktop replacement for Microsoft Project, being able to open  existing native Project files. It was developed by Projity in 2007.  OpenProj runs on the Java Platform, allowing it to run on a variety of  different operating systems.

[http://sourceforge.net/projects/openproj/](http://sourceforge.net/projects/openproj/)


```

wget http://nchc.dl.sourceforge.net/sourceforge/openproj/openproj_1.4-2.deb && sudo dpkg -i openproj_1.4-2.deb
```

Also you are going to need to install the actual Sun Java PPA from this list to get it to run:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

