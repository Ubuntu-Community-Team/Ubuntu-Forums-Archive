---
title: "I screwed over my core system"
date: 2006-01-28
forum: General Help
---

### Post by Therrol on 2006-01-28
Ok, so I just reinstalled my computer to ubuntu breezy. I opted for the server installation. and installed a few important things. long story short, I wanted a newer version of firefox, but it needed a new version of libdc++6 wich was not in the breezy repositories. I installed the one from dapper. Now I tried to install ubuntu-artwork and it shows me some broken packages so I apt-get -f install. This removed firefox. Why? Because it needed the old version of gcc.

cpp is also removed.

Is there a way I can downgrade my packages to the breezy ones? How can I install the new fluxbox?

---

### Post by musther on 2006-01-29
Yeah, there's a dependency issue when installing firefox 1.5 on breezy, there's a tutorial or howto somewhere on the forums which tells you to download and then modify the dependencies of the package (giving it a different lib).  I did as it said, it worked fine, so I suggest searching for firefox 1.5 in the forums.

Good luck

---

### Post by Elvish Legion on 2006-01-29
Try automatix

---

