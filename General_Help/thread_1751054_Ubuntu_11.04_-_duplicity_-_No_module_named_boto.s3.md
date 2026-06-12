---
title: "Ubuntu 11.04 - duplicity - No module named boto.s3.key"
date: 2011-05-06
forum: General Help
---

### Post by nworbnhoj on 2011-05-06
I was using duplicity to backup to Amazon s3 in Ubuntu (10.10)

The upgrade to Ubuntu 11.04 caused my backups to fail with an error message containing "No module named boto.s3.key"

The solution was to use Synaptic to install python-boto.

[LIST]
[*]open Synaptic Package Manager,
[*]search on "boto",
[*]Mark "python-boto" for installation
[*]Apply
[/LIST]
good luck

---

