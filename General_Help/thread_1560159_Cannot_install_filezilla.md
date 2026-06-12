---
title: "Cannot install filezilla"
date: 2010-08-24
forum: General Help
---

### Post by pmulgaonkar on 2010-08-24
Cannot install filezilla


For the last two days, I have been trying to install Filezilla from the standard distributions. I get an error:
Quote:
> Failed to fetch [http://archive.getdeb.net/ubuntu/poo...etdeb2_all.deb](http://archive.getdeb.net/ubuntu/poo...etdeb2_all.deb) 404 Not Found


Any idea what is wrong?

---

### Post by cdenley on 2010-08-24
Why are you using getdeb? It is in the ubuntu repos.

I'm guessing you're trying to install an old version which no longer exists in getdeb's repos because your package index is outdated.
```

sudo apt-get update
sudo apt-get install filezilla

```

---

