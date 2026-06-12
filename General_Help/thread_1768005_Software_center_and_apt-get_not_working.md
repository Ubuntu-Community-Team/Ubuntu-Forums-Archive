---
title: "Software center and apt-get not working"
date: 2011-05-26
forum: General Help
---

### Post by c0dege3k on 2011-05-26
I can get the main page in the software center, but nothing else, and the terminal gives me this output whenever I do apt-get install *whatever*

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Why might this be happening?

---

### Post by Rubi1200 on 2011-05-26
Hi,

try this and let us know what happens:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by c0dege3k on 2011-05-26
That worked! Thanks a ton

---

### Post by Rubi1200 on 2011-05-26
> **c0dege3k said:**
> That worked! Thanks a ton
No problem, you are more than welcome :-)

---

