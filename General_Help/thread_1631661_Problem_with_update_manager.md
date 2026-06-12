---
title: "Problem with update manager"
date: 2010-11-26
forum: General Help
---

### Post by dsantesteban on 2010-11-26
Every time I run update manager (ubuntu x64 10.10), I get an error saying "Failed to download repository information, check your internet connection" and "W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DA360C64005E0276, W:Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead." in the details.

Whats weird though is that I still get updates, yet it doesnt change the last day i updated the package information.

I looked around a bit but none of the previous solutions seem to work. Anybody smarter than me know the issue and how to fix it?

---

### Post by Foxheadz on 2010-11-26
did you try just removing those sources?

---

### Post by dsantesteban on 2010-11-26
wow, i feel like an idiot. in other words, it worked. thanks!

---

### Post by Foxheadz on 2010-11-26
Lol no problem i pretty much did the same thing when i started with ubuntu

---

### Post by dsantesteban on 2010-11-26
How can i continue to update Skype though?

---

### Post by Foxheadz on 2010-11-26
Find the updated source if there is one because the source you had pretty much didnt exist

---

