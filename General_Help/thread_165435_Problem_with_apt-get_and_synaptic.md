---
title: "Problem with apt-get and synaptic"
date: 2006-04-24
forum: General Help
---

### Post by duf on 2006-04-24
A while ago i installed (or tried to install) Corel graphics9, i tried to remove the package and now i get the following errors when I run apt-get install -f

"Removing menusupport-kde-corel ...
chmod: cannot access `/etc/menu-methods/kde-corel-simple': No such file or directory
dpkg: error processing menusupport-kde-corel (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 menusupport-kde-corel
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

I cannot install or update any packages. Using the "fix broken" doesn't help either.

Anyone have a solution with apt or dpkg?

Thanks

---

### Post by Ensnared on 2006-04-24
Well, one thing you can try is to create the file it's trying to remove - I've had similar errors happen before, and creating the file in question tends to solve it.

So - first confirm that it doesn't exist, and if it doesn't, just do this:```
sudo touch /etc/menu-methods/kde-corel-simple
```...and then try "apt-get -f install" again.

There may be cleaner ways to do it but I'm not aware of them. Personally I think it's plain stupid for something like this to produce a critical error; why is it unable to continue if the whole problem is that a file it's trying to remove, is already gone? :rolleyes:

---

### Post by duf on 2006-04-24
Thanks
It worked for that file but now i have abother to remove. Hope I  don't get a lot

---

