---
title: "ubuntu breaks windows boot."
date: 2010-02-14
forum: General Help
---

### Post by rock4christ on 2010-02-14
Whenever I boot into ubuntu it seems to break windows so that it cant start(have to run startup repair and system restore)

---

### Post by rock4christ on 2010-02-14
got it fixed. apparently automounting my windows drive causes problems, so I unmounted it, and removed the pack file in /var/lib/ureadahead/

---

