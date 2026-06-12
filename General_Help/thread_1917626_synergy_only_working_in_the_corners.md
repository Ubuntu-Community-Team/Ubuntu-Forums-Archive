---
title: "synergy only working in the corners"
date: 2012-01-30
forum: General Help
---

### Post by jasonlfunk on 2012-01-30
Hello,
I am running Ubuntu 11.10 with Unity and also running Synergy (the network KVM). I have two systems set up with my ubuntu system being the server. I have the other system positioned to the right of the ubuntu system. I can only move to the right system by going through the upper and lower right hand side and not through the right edge itself. I can come back to the ubuntu system through the whole edge. I hope that is clear.

What could be preventing the right edge from being detected by synergy? I thought it might Unity/Compiz but I can't find any setting in the compiz settings manager that would be preventing it.

---

### Post by cptcoconut on 2012-01-30
I was just looking into the same issue, and found the following bug report (with patch): [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/875170]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/875170")

---

### Post by jasonlfunk on 2012-01-31
Perfect. Thanks!

---

