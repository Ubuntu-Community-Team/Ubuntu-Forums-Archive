---
title: "Panic: chmod deleted my music library?!?"
date: 2009-12-30
forum: General Help
---

### Post by reader4 on 2009-12-30
I was having trouble using firefly to serve music, and found that the problem was that most of my library had 600 permissions.  So, I used chmod -R 644 and now all of my files are missing!  Most I have backed up (hence the original 600 problem) but there are nearly 1000 that I added recently.  Any chance of recovery?  Why would this happen?

---

### Post by taurus on 2009-12-30
If you change the directories to rw only, then you cannot change to them.  What you want for directories are rwx--7.  Meanwhile, files can be rw--6.

```
chmod -R 755
```

---

### Post by reader4 on 2009-12-30
Yes, after thinking about it for a bit, I realized that as root I could see everything and that, as you said, the directories were all changed.  Whew - thanks for the reply.

---

### Post by jamesisin on 2009-12-30
If this is solved, please mark it as such (in Thread Tools above).

---

