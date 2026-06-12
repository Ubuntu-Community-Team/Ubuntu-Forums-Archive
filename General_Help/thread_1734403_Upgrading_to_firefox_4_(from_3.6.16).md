---
title: "Upgrading to firefox 4 (from 3.6.16)"
date: 2011-04-20
forum: General Help
---

### Post by christian_bach on 2011-04-20
Hi,

I'm trying to upgrade my firefox installation to version 4. But it seems there are slight problems.

What I did was:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```

In a CLI.

When I open firefox it's still the old version.

If I in a terminal write firefox -v it tells me it's version 4.

What am I missing here?

---

### Post by ChrisWells on 2011-04-20
Try rebooting?

---

### Post by christian_bach on 2011-04-20
> **ChrisWells said:**
> Try rebooting?
Ahh, the good old reboot trick worked.

The odd thing is I'm pretty sure all firefox processes was killed.

Well it works now. Please mark this as solved.

Thanks. :D

---

### Post by Frogs Hair on 2011-04-20
Use the thread tools on the top of the page to mark the thread solved.

---

### Post by christian_bach on 2011-04-20
> **Frogs Hair said:**
> Use the thread tools on the top of the page to mark the thread solved.
Ty.

Didn't notice that feature.

---

### Post by lovinglinux on 2011-04-21
For future reference, see [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

