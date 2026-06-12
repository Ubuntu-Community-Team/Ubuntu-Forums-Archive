---
title: "Apache2 Fancy Listing"
date: 2009-11-23
forum: General Help
---

### Post by cantdrive55 on 2009-11-23
I had setup fancyindexing with my old apache2 setup but I cant for the life of me get it working on the new one today. Where do I need to put in the FancyIndexing option?

---

### Post by rudy.b on 2009-11-23
My Apache setup had FancyIndexing by default, but you should be able to add it by enabling the autoindexing module: 

```
sudo a2enmod autoindex
```

(be sure to restart your Apache server after enabling it)

If that doesn't work, be sure your /etc/apache2/mods-available/autoindex.conf file includes the FancyIndexing option with the IndexOptions directive.

---

