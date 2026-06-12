---
title: "encfs mount directory disappears"
date: 2011-06-15
forum: General Help
---

### Post by k94382 on 2011-06-15
whenever I mount a encfs directory to a regular directory, the regular directory disappears. this is the command I use

encfs ~/encrypted ~/plain

when I try to access the folder from my windows computer, I can not see it. what to do?

---

### Post by k94382 on 2011-06-17
suggestions?

---

### Post by k94382 on 2011-06-17
never mind, I found that I needed this

encfs "encrypted folder" "mount folder" -- -o allow_other

---

