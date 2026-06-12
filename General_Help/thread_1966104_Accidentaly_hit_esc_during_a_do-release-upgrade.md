---
title: "Accidentaly hit esc during a do-release-upgrade?"
date: 2012-04-26
forum: General Help
---

### Post by haziz on 2012-04-26
While doing a do-release-upgrade (from 11.10 to 12.04), I accidentally hit esc and noticed that this interrupted the download of the file being donwloaded at the time and then skipping to the next file. One of those files is coreutils, the other is lbssl1.0.0.

Will do-release-upgrade or apt-get reattempt a download of those files before attempting the upgrade?

I presume the install script and software is robust enough to note the dependencies and to reattempt download of those files? The process is still ongoing as I type this.

---

### Post by NoNameWill on 2012-04-26
When it is finished it will suggest you do a 

```
sudo apt-get update --fix-missing
```

---

