---
title: "rdiff-backup"
date: 2011-09-14
forum: General Help
---

### Post by steevven1 on 2011-09-14
I am using rdiff-backup with the "--override-chars-to-quote" flag. It works in keeping rdiff-backup from making escape sequences out of all the characters I specify EXCEPT hyphen (-). Has anyone found a solution to this? Thanks.

---

### Post by steevven1 on 2011-09-14
SOLVED! As explained here: [http://bend-ing.blogspot.com/2008/07/beware-of-dash-character-in-regular.html](http://bend-ing.blogspot.com/2008/07/beware-of-dash-character-in-regular.html)

You have to put the dash in brackets: [-] otherwise it specifies a range.

---

