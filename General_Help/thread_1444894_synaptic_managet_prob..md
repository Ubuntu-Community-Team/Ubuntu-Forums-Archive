---
title: "synaptic managet prob."
date: 2010-04-01
forum: General Help
---

### Post by nischalinn on 2010-04-01
My synaptic shows:

[B]E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/B]
What to do with this problem?

---

### Post by NCLI on 2010-04-01
Could you please upload /etc/apt/sources.list as an attachment?

---

### Post by 3rdalbum on 2010-04-02
> **nischalinn said:**
> My synaptic shows:

[B]E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)

If you've recently modified the /etc/apt/sources.list file to add an extra repository, then you've probably done the modification wrong. You can either open the file again and try and fix the error:

```
gksudo gedit /etc/apt/sources.list
```

The error is on line 58 of the file.

If you don't realise where you've gone wrong, then you can delete the line, or "comment it out" by putting a # symbol at the start of the line. Any lines with # at the beginning will not be read by the computer.

Save your changes and reload the package list ("sudo apt-get update" or click Reload in Synaptic).

In future, use System > Administration > Software Sources to add new repositories; it will not add any lines that are malformed.

---

