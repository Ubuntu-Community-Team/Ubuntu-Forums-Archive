---
title: "help me stick it to the &quot;MAN&quot;- pages"
date: 2009-08-11
forum: General Help
---

### Post by xaegis on 2009-08-11
I suspect I have corrupted man pages Because I'm getting this error:

```

/usr/bin/mandb: only 8 fields in content
/usr/bin/mandb:  index cache /var/cache/man/4890 corrupt

```

How can I fix this problem. I tried reinstalling the man pages to no avail.
Any suggestions on how to procede?

:)

---

### Post by Glyndwr on 2009-08-11
I've never seen that before.  You could try running catman.

---

### Post by mapsight on 2009-08-28
I had the same error, so I deleted the cache index:

```
sudo rm /var/cache/man/index.db
```

I'm not sure how you re-create the index manually, but when you install/update something that has man pages, the system should re-create the index automatically.

---

### Post by CryNGRoad on 2010-02-28
I recently fixed this problem by running:
```
sudo mandb -c
```Which re-creates all the man page databases.

See the man page for mandb (assuming it's not corrupted;))

---

