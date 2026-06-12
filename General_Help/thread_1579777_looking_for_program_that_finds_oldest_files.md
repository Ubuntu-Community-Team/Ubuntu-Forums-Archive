---
title: "looking for program that finds oldest files"
date: 2010-09-22
forum: General Help
---

### Post by Arminius on 2010-09-22
got a whole lot of video files spread among 100's of folders, wondering if Linux has a program that can scan the modification and view dates of them all, and just display what's been accessed most recently.
And what hasn't been accessed in years?

---

### Post by sidzen on 2010-09-22
Look here, please:  [http://content.hccfl.edu/pollock/unix/findcmd.htm](http://content.hccfl.edu/pollock/unix/findcmd.htm)
or [here]("http://www.gnu.org/software/findutils/manual/html_mono/find.html#Overview"), under "2 Finding Files" is probably better

---

### Post by Arminius on 2010-09-22
bit complicated all that, was hoping there was software that could just simplify it all

---

### Post by Arminius on 2010-09-25
bump

---

### Post by The Cog on 2010-09-25
```
find ~ -name '*.mp4' -exec ls -l {} \; | sort -k 6 > sortedlist.txt
```
Use your favourite file editor to view the created list.

---

