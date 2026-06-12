---
title: "Indexing"
date: 2010-07-07
forum: General Help
---

### Post by hatewindows on 2010-07-07
Hello all--is there a way to disable indexing on 10.04?

---

### Post by WorMzy on 2010-07-07
If you mean the updatedb that runs daily, you can delete the mlocate job from etc/cron.daily with 'sudo rm /etc/cron.daily/mlocate', but it may only be necessary to remove executable permissions from it with 'sudo chmod -x /etc/cron.daily/mlocate'.

---

### Post by luigi_mb on 2010-07-07
> **hatewindows said:**
> Hello all--is there a way to disable indexing on 10.04?

If you mean Tracker (or Beagle), you can uninstall them using Synaptic.

/luigi

---

