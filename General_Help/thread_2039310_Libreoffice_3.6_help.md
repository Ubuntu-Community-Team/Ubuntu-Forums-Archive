---
title: "Libreoffice 3.6 help"
date: 2012-08-08
forum: General Help
---

### Post by Primefalcon on 2012-08-08
I installed the libreoffice 3.6 today and amd gettingthe following error when I try to launch it

```
file:///opt/libreoffice3.6/program/../share/extensions/script-provider-for-python/components.rdb: duplicate <implementation name="org.openoffice.pyuno.LanguageScriptProviderForPython">
terminate called after throwing an instance of 'com::sun::star::uno::DeploymentException'
```

I am tempted to remove it and search for a ppa raher than go back to 3.5 thats in 12.04 unless someone knows a fix for this particular issue...

---

### Post by Primefalcon on 2012-08-08
nvm fixed the issue by wiping user config for it.... figured that was worth a shot

rm -R ~/.config/libreoffice/

---

### Post by vasa1 on 2012-08-09
> **Primefalcon said:**
> nvm fixed the issue by wiping user config for it.... figured that was worth a shot

rm -R ~/.config/libreoffice/

But that means you lose your settings?

---

### Post by Primefalcon on 2012-08-15
> **vasa1 said:**
> But that means you lose your settings?
yeah it did. unfortunately it must of been a setting in there that was not compatible between 3.5.5 and 3.6, and those settings are pretty easily set back up anyhow

---

