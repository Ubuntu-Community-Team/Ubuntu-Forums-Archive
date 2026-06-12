---
title: "Cluster Computing Programs?"
date: 2011-03-28
forum: General Help
---

### Post by williamwade on 2011-03-28
If I was to set up a Cluster, I know it wouldn't make much difference to loading up my browser, but would all heavy duty programs (Video Encoders mainly) work with it, or would I need to use programs specifically designed for cluster use?

---

### Post by blind2314 on 2011-03-28
For an active/passive cluster system (failover capabilities, not parallel computing), the application doesn't have to be designed for it, the cluster software simply has to be able to handle it.
 
For parallel clustering, which is what you're talking about, the application has to be specifically designed to work that way or at least have an option to run in a parallel mode. If not, it won't work.

---

