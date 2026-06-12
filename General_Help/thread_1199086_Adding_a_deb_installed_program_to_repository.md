---
title: "Adding a deb installed program to repository"
date: 2009-06-28
forum: General Help
---

### Post by tstack77 on 2009-06-28
I installed a .deb version of Deluge on my server that was not yet released in the ubuntu repositories (newer version had webUI). Of course, now that version is quite outdated and deluge has created their own repository, so I want to get it back on that repository list. 

I added the deluge-specific repositories to sources.list and installed the signing key, but when I try to upgrade I get:

```
The following packages have been kept back:
  deluge-torrent linux-image-server linux-server
```

How do I force the issue without purging deluge (I'd hate having to reconfigure everything)?

-axel

---

### Post by tstack77 on 2009-06-29
bump!

---

### Post by mcduck on 2009-06-29
As the package was installed from a .deb package it's already registered in apt's database, just like if it was installed from a repository.

There must be some other reason why it's not upgrading.
Try this:
```

sudo apt-get update && sudo apt-get dist-upgrade
```

---

