---
title: "Where do PPA's install to?"
date: 2010-09-17
forum: General Help
---

### Post by lukemk1 on 2010-09-17
So I have a question. The way PPA's work when you add a repo using sudo add-apt-repository ppa:<repository-name> is the same way if you were to edit the source.list file itself? Because when I look at the source file I don't see anything being added to it. So is it updating some other file or something? I want to know that way I know which file I need to back up so I can go about reinstalling packages if something goes wrong.

---

### Post by Elfy on 2010-09-17
Check in here and you will find the source lists from the PPAs

/etc/apt/sources.list.d

---

### Post by lukemk1 on 2010-09-19
So if I was to back that file up and reinstall my system and then put my backed up file in place of the freshly installed on all of my old PPA's would be installed, correct?

---

