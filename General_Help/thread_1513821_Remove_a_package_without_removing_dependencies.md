---
title: "Remove a package without removing dependencies"
date: 2010-06-20
forum: General Help
---

### Post by BeWop on 2010-06-20
I need to remove libgl1-mesa-swx11, as after I installed it, it has slowed down all my graphics. However, in SPM, it says in order to remove it, I have to remove most of my system, it seems as though it's "dependencies" involve everything to do with graphics,  which I was running fine and much better before.

So, how do I remove this package without removing dependencies?

---

### Post by dv3500ea on 2010-06-20
By dependencies, do you mean packages that libgl-mesa-swx11 depends on or packages that depend upon it. 

You can't uninstall a package without uninstalling all packages that depend on it. 

Just uninstalling it normally shouldn't remove any packages it depends on.

---

### Post by James78 on 2010-06-20
How do you remove it without removing the dependencies?

```
sudo dpkg -r --force-all libgl1-mesa-swx11
```
or (purge everything, I prefer this way)
```
sudo dpkg -P --force-all libgl1-mesa-swx11
```

**[COLOR="Red"]WARNING:: Doing this will probably make your system unusable, DO NOT ATTEMPT UNLESS YOU UNDERSTAND THIS. Don't blame me if your system breaks.[/COLOR]**

---

### Post by BeWop on 2010-06-20
> **James78 said:**
> How do you remove it without removing the dependencies?

```
sudo dpkg -r --force-all libgl1-mesa-swx11
```
or (purge everything, I prefer this way)
```
sudo dpkg -P --force-all libgl1-mesa-swx11
```

**[COLOR="Red"]WARNING:: Doing this will probably make your system unusable, DO NOT ATTEMPT UNLESS YOU UNDERSTAND THIS. Don't blame me if your system breaks.[/COLOR]**

Thanks, this did the trick. Everything's working again.

---

