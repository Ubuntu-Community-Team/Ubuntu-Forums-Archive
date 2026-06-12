---
title: "Needing help with CVS"
date: 2006-02-22
forum: General Help
---

### Post by OldRod on 2006-02-22
Disclaimer:  I am totally new to Linux, so I need help :)

I have a couple of programming projects that I work on frequently in a Windows environment.  I use TortoiseCVS under Windows to access the source repository for those projects.  Last night I installed Ubuntu on a second machine and want to start working in Linux on those same projects.  I added the CVS package to my Ubuntu install and it installed fine, but I'm not sure how to actually use it.

I'm assuming I have to go to the terminal window and type cvs commands directly in order to download the source for the projects I'm working on, but does someone have an idiot's guide on how to do this in Ubuntu? :)

Thanks in advance!

---

### Post by lamego on 2006-02-22
Basic commands are:
  cvs -z3 -dYOUR_CVS_ROOT checkout project

When you need to update your copy, get into the working directory and:
  cvs update

If you need to apply your changes to the "central" version:
  cvs commit

If you need to add a file:
 cvs add file

---

### Post by OldRod on 2006-02-22
Thanks, I'll give that a try :)

---

