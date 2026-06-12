---
title: "How to search for files starting with f?"
date: 2009-11-27
forum: General Help
---

### Post by dandeliondream on 2009-11-27
In ubuntu terminal, i have tried
$ find ^f
(i assume it to find files that begin with f... but in vain)

please assist me, thank you

---

### Post by Aearenda on 2009-11-27
The find command needs a number of parameters. Variations on the documentation can be seen by typing```
man find
```or```
find --help
```or ```
info find
```

I think this will do what you say you want, but it might return rather more than you expect since it searches in hidden subfolders too:```
find . -name "f*"
```
You can use '-iname' for case insensitive searching. The '.' says 'look in the current directory'.

---

### Post by tjwilli on 2009-11-27
> **Aearenda said:**
> The find command needs a number of parameters. Variations on the documentation can be seen by typing```
man find
```or```
find --help
```or ```
info find
```

I think this will do what you say you want, but it might return rather more than you expect since it searches in hidden subfolders too:```
find . -name "f*"
```
You can use '-iname' for case insensitive searching. The '.' says 'look in the current directory'.

If you want to limit your search to just regular files:

```
find  . -type f -name f\* 
```

---

### Post by Dennis N on 2009-11-27
This will do for one directory:

If current directory is to be searched:

```
ls f*
```

---

### Post by dandeliondream on 2009-11-28
> **Dennis N said:**
> This will do for one directory:

If current directory is to be searched:

```
ls f*
```
that is what i wanted. thanks!

---

### Post by dandeliondream on 2009-11-28
> **tjwilli said:**
> If you want to limit your search to just regular files:

```
find  . -type f -name f\* 
```
I've learnt something new today...thanks!

---

