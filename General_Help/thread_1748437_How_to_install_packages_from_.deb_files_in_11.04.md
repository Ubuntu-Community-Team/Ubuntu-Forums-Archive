---
title: "How to install packages from .deb files in 11.04"
date: 2011-05-03
forum: General Help
---

### Post by apoorvumang on 2011-05-03
If a certain package is there in the repository and I try installing the same using a .deb file that I already have, it always downloads the packages again.

I'm trying to install the packages by just double-clicking them, and then selecting install in Ubuntu Software Centre that opens up (it gives a warning saying that 'Only install if you trust the source'). 

Is there a way to do this so that I do not have to download the packages again?

---

### Post by snowpine on 2011-05-03
In general it is always safest to install applications from the Ubuntu repositories using a package manager (such as Ubuntu Software Center). This ensures that you'll install only signed packages from trusted sources.

That being said, the terminal command to install a .deb file is:

```
sudo dpkg -i /path/to/the/file.deb
```

Some people prefer to use the GUI "gdebi" application.

---

### Post by perspectoff on 2011-05-03
If you downloaded a .deb package, just click on it in the Nautilus file manager (or whatever they use these days in Unity). That will install it using GDebi automatically. 

Don't use Synaptic Package manager for .deb packages that you have already downloaded.

---

### Post by apoorvumang on 2011-05-04
Thanks! Apparently, 11.04 doesn't ship with Gdebi.

---

