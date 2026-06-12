---
title: "Cancelled download's leftover files"
date: 2012-05-04
forum: General Help
---

### Post by sobakasu on 2012-05-04
I just cancelled a somewhat lengthy install via the software center in favor of a terminal install, now I want to delete the already downloaded/leftover files from the first installation try.

Could anybody tell me where these files are located so I can delete them manually? In case, of course, aborted downloads' files are purged automatically!

Thanks! :)

---

### Post by codemaniac on 2012-05-04
As long as i remember all the downloaded .deb files recides in the directory **/var/cache/apt/archives** .You can delete them manually from there .

---

### Post by sobakasu on 2012-05-05
Ahh, I see, thank you very much, I didn't know that yet! :)

Surprisingly, it's already pretty crowded in there -- I assume it's OK to clean up there a little once in a while (e.g. the files are not necessarily used by any program still)?

---

### Post by zombifier25 on 2012-05-05
Run this command in the terminal.
```
sudo apt-get clean
```
It will clean that folder for you.

---

### Post by codemaniac on 2012-05-05
> **sobakasu said:**
> Ahh, I see, thank you very much, I didn't know that yet! :)

Surprisingly, it's already pretty crowded in there -- I assume it's OK to clean up there a little once in a while (e.g. the files are not necessarily used by any program still)?

You can purge them off , because they are already installed in your system .In case if you ever need them , you can make archive of them and then clean the directory .

---

### Post by sobakasu on 2012-05-05
Thanks you guys, great help!

---

