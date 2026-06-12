---
title: "HTML app, Bluefish"
date: 2010-10-17
forum: General Help
---

### Post by Legeril on 2010-10-17
I've just downloaded and installed an app, Bluefish. It was recommended  to me on another computer board, and after a lot of abuse someone  finally posted a link to this app. I got a few errors while performing  "sudo pet-get update", namely these 

```
Err http://debian.wgdd.de lucid/multiverse Packages
  404  Not Found
W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://debian.wgdd.de/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```Will these errors cause a big problem? The program seems to run ok, has  anyone used this app before? Did you like it? Any other recommendations?

I'm a very very part-time web designer, I'm only doing a website for a friend as a favour. Other than that I really don't code at all, I'm looking for an app with WYSIWYG and coding windows.

---

### Post by stoneage on 2010-10-17
Those errors are not related to Bluefish, it is apt not finding some of the repositories on your sources.list

Try setting your software source to a different server, then update the list.

---

