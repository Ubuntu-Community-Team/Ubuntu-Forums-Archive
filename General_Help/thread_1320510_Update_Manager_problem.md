---
title: "Update Manager problem"
date: 2009-11-09
forum: General Help
---

### Post by Minsky on 2009-11-09
When running Update Manager, I get the following error message:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.bz2  Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-amd64/Packages.bz2  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.
```

Does this mean that I cannot receive critical updates, and does anyone know of a solution for this?

---

### Post by The Funkbomb on 2009-11-09
I'd try another server.

System>Administration>Software Sources.

On the first page, click the server, choose other and let Ubuntu pick the best server for you.

If it still happens, then the problem is clearly on your end and we can investigate further.

---

### Post by Minsky on 2009-11-09
Nice one Funkbomb, that did the trick. Thanks.

---

