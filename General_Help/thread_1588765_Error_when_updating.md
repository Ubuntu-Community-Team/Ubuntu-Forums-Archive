---
title: "Error when updating"
date: 2010-10-05
forum: General Help
---

### Post by jakupl on 2010-10-05
When I do sudo apt-get update, this is what I get:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  lucid-backports/source/Sources in Meta-index file (malformed Release file?)

Any suggestions?

---

### Post by jakupl on 2010-10-06
bump

---

### Post by plucky on 2010-10-06
> **jakupl said:**
> When I do sudo apt-get update, this is what I get:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  lucid-backports/source/Sources in Meta-index file (malformed Release file?)

Any suggestions?

Try a different server (**System > Administration > Software Sources**) or un-tick the Lucid Backports under the Updates tab in Software Sources.

Good Luck

---

