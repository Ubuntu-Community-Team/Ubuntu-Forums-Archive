---
title: "Ubuntu 8.04 failing to free memory"
date: 2011-10-18
forum: General Help
---

### Post by Bucky24 on 2011-10-18
We have a virtual server slice running Ubuntu 8.04.4 LTS that has encountered an interesting issue recently.

After having the slice crash several times due to running out of both memory and swap space, I began monitoring the output from top and ps. After noticing that two apache processes were taking up 1.2 GB (600 MB each), I killed the apache daemon. Before killing the daemon, the server was using 1.4 GB of memory. This did not change after I killed the daemon and did not go down until I rebooted the slice.

I verified that no other processes were taking the memory. Does anyone know why Ubuntu/apache is failing to free up this memory?

---

