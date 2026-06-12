---
title: "Problems with Software Centre and Synaptic Package Manager"
date: 2011-03-29
forum: General Help
---

### Post by w33t on 2011-03-29
Neither the Software centre or package manager will open. its rather upsetting.
The software centre gives me nothing to work with but when i open the package manager i get this error:

E: Type ‘nchpad.net/ubuntu-wine/ppa/ubuntu’ is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

i know that tells me exactly what i need to to but if someone could be so kind to give me step by step instructions to get this fixed it would be greatly appreciated. im new to ubuntu and its my primary os so i really need this fixed.

---

### Post by mikewhatever on 2011-03-29
Here is a quick and dirty way:
```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list

sudo apt-get update
```

That will delete the wine ppa, but if you want to edit the file manually, use the following command:

```
gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list

sudo apt-get update
```

---

### Post by w33t on 2011-03-29
> **mikewhatever said:**
> Here is a quick and dirty way:
```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list

sudo apt-get update
```That will delete the wine ppa, but if you want to edit the file manually, use the following command:

```
gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list

sudo apt-get update
```


i tried the first. i got an error saying:

rm: cannot remove '/etc/apt/sources.list.d/ubuntu-wine-ppa-mavrick.list': No such file or directory

=[

---

### Post by w33t on 2011-03-29
i tried to update and i got an error saying:

E: Type "nchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources/list.d/ubuntu-wine-ppa-mavric.list
E: The list of sources could not be read.

---

### Post by mikewhatever on 2011-03-29
Odd, let's see the output of the following:
```
ls /etc/apt/sources.list.d/
```

---

### Post by oldos2er on 2011-03-29
> **w33t said:**
> i tried the first. i got an error saying:

rm: cannot remove '/etc/apt/sources.list.d/ubuntu-wine-ppa-mavrick.list': No such file or directory

There's a typo, it's "mav[COLOR="Red"]e[/COLOR]rick"

Use Tab completion in the shell to save yourself some typing.

---

