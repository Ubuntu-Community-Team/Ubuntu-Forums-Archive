---
title: "problem with updates"
date: 2010-12-09
forum: General Help
---

### Post by xXDestroyerGRXx on 2010-12-09
I try to update from update manager and i reload and it gives me this error:

```
W:Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

what i do?

---

### Post by sikander3786 on 2010-12-09
404 Error means server not found. And that is happening here in case of Launchpad PPAs. Remember, maintaining a PPA is often upto a single person and therefore, problems like this seem to happen with those PPAs quite regularly.

Go to Software Center > Edit > Software Sources > Other Software Tab and disable the offensive PPAs and reload the repository information or,

```
sudo apt-get update
```

---

### Post by xXDestroyerGRXx on 2010-12-09
Thanks it worked now.!

---

### Post by sikander3786 on 2010-12-09
Glad to know the issue is solved.

You can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

