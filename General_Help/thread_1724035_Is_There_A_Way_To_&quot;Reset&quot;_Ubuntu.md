---
title: "Is There A Way To &quot;Reset&quot; Ubuntu?"
date: 2011-04-07
forum: General Help
---

### Post by Funklink on 2011-04-07
Is there a way to "reset" ubuntu to when you installed it? My Ubuntu won't let me install packages. I get an error that says it cannot find the selected packages and then I click okay and it says "installed" but obviously, it wasn't.

---

### Post by Lolpanda on 2011-04-07
If when you installed Ubuntu you put /home on a separate partition, you should be able to pop the CD back in. Install it with custom partitioning. Format / as (probably) ext4. Give it the mount point /, then whichever partition is /home, DON'T format it, but give it the mount point /home.

That will reset Ubuntu completely except for your documents and personal settings, which I dont think involve apt/aptitude.


This is all assuming you installed Ubuntu by hand and didn't just go with defaults. Maybe one of the dev's can give a shoutout on whether the default partitioning does everything to / or splits up / and /home

---

### Post by zvacet on 2011-04-07
```
sudo apt-get update && sudo apt-get upgrade
```

If you get any errors post it here.Same for installing package.

```
sudo apt-get install <packagename>
```

---

