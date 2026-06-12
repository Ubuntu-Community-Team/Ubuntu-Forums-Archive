---
title: "unattended installation of package"
date: 2011-06-05
forum: General Help
---

### Post by jnyrup on 2011-06-05
Does anyone know how to automatic accept the EULA for ttf-mscorefonts-installer?

---

### Post by TeoBigusGeekus on 2011-06-05
You could try piping it through the yes command, ie.
```
sudo apt-get install ttf-mscorefonts | yes
```

---

### Post by jnyrup on 2011-06-05
> **TeoBigusGeekus said:**
> You could try piping it through the yes command, ie.
```
sudo apt-get install ttf-mscorefonts | yes
```

Ufortunately that didn't helped it just spit put y's

But found a solution even though it's a bit dirty dirty :D.

Installed the packages
Opened /var/cache/debconf/config.dat to what was changed.
Made a script that appended the necessary lines to config.dat

```
echo -e "Name: msttcorefonts/accepted-mscorefonts-eula\nTemplate: msttcorefonts/accepted-mscorefonts-eula\nValue: true\nOwners: ttf-mscorefonts-installer\nFlags: seen\n" | sudo tee -a /var/cache/debconf/config.dat
```

The dirty part is that when I run ```
sudo apt-get install ttf-mscorefonts-installer
``` it registers that config.dat is not sorted and tries to repair it. Now it looks if I had accepted the EULA in the installer.

---

