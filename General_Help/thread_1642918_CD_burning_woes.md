---
title: "CD burning woes"
date: 2010-12-11
forum: General Help
---

### Post by fabzzap on 2010-12-11
I tried burning CDs from .iso images with Brasero several times, but never successfully. Every time I used md5sum or sha256sum to verify the integrity of the CD, an I/O error occurred.

I then tried the command-line tools: wodim, cdrskin, even cdrtools (downloaded source and compiled). They give the same result: the CD works if recorded with -sao, and does not if recorded with -tao.

Now, not being able to read CDs written with track-at-once is a minor annoyance, and I wish I had a solution for it. Yet, the major anoyance is not being able to force Brasero to use session-at-once. Is there any menu or preference to be set anywhere?

---

