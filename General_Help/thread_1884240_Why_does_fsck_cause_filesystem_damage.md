---
title: "Why does fsck cause filesystem damage?"
date: 2011-11-20
forum: General Help
---

### Post by abtekk on 2011-11-20
Why/how does fsck cause filesystem damage on a mounted system?

It's not important, I'm just curious.

---

### Post by lisati on 2011-11-20
When a utility such as fsck is going about its business exclusive access is desirable. Imagine this scenario: fsck finds something to fix and is part way through putting things right when another program decides to write to disk. The risk is that what actually gets written to disk reflects the intent of neither program. Result: major hassle.

---

