---
title: "wget help"
date: 2009-10-07
forum: General Help
---

### Post by zeropointorigin on 2009-10-07
Hey, I just have a quick question. I'm attempting to learn how to use wget, but it doesn't seem to be recursively digging through the directories. The full command I'm using is:

wget --wait=20 --limit-rate=20k --convert-links --no-clobber --page-requisites --recursive -l 0 -p -U Mozilla websitegoeshere.com

What might I be doing wrong?

---

### Post by geirha on 2009-10-07
wget doesn't automatically know how the directory structure is. If there's no links to files inside foo/ in index.html, then it will not download anything inside foo/.

---

