---
title: "File Browsing Stalls and abuse CPU"
date: 2009-12-28
forum: General Help
---

### Post by zelhar on 2009-12-28
When I try to browse through directories in native kde/qt application including the default kubuntu file browser, I have to wait for a minute or so while the cpu works extra hard and occasionally i get a program crash.

When I use none kde/qt application it uses a different file browser and then it loads the directory instantaneously. 

Is this bug known, and what can I do ?

---

### Post by zelhar on 2010-01-02
I discovered the source of the problem: 
A file with the name form "name.desktop"

I changed the name, and the problem was solved.

---

