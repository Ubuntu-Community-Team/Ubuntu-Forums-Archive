---
title: "/usr/local/etc has been overwritten - how do I re-install only this directory?"
date: 2006-02-12
forum: General Help
---

### Post by Roobert on 2006-02-12
I think I overwrote my /usr/local/etc directory using a sudo mv command. At any rate, when I ls -l, it's not prefixed by a 'd' in the permissions. Is there a command to re-install only this part of Ubuntu, or do I meed to reinstall the whole OS again?

---

### Post by zxee on 2006-02-12
Provided that you hadn't changed/customized that directory you could get it back by booting from the live cd opening a terminal doing  'cp /etc/usr/local' to the partition that holds your install. Hope that helps.

---

### Post by engla on 2006-02-12
I'm not totally sure what you are after, but in my Ubuntu install, there is no directory "/usr/local/etc" by default, hence the only thing you might have lost are custom installs, nothing from the default install.

---

### Post by astoltz on 2006-02-12
[QUOTE=Roobert]At any rate, when I ls -l, it's not prefixed by a 'd' in the permissions.[/QUOTE]Do you mean that /usr/local/etc is still there it's just not identified as a directory?

---

