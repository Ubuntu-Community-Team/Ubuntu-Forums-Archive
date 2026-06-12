---
title: "LVM2: Move PV partition within HDD"
date: 2011-12-23
forum: General Help
---

### Post by Anton K on 2011-12-23
Hello all,


I need to move LVM2 physical volume further within HDD. As for now partition table looks like:

[FONT=Courier New][10GB] [ PV ~500GB ] [... Free space ...][/FONT]

And I want to make:

[FONT=Courier New][50GB ...] [ PV ~500GB ] [Free space ...][/FONT]

Not sure how to do this. I believe tools [FONT=Courier New]pvmove[/FONT] and [FONT=Courier New]pvresize[/FONT] can solve the task but have no idea how to apply them for this particular purpose. [FONT=Courier New]KVPM[/FONT] tool has an ability to perform such operations, but it doesn't allow to do this in my case.


Thank you for reading, any ideas and hints are appreciated.
Anton.

---

### Post by Anton K on 2011-12-26
The only solution I have found is to move all physical extents from a HDD before partitioning it.

However this way is unlikely the fastest and the optimal one.

---

