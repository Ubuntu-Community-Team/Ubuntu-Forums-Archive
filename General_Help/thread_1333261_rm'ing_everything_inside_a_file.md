---
title: "rm'ing everything inside a file"
date: 2009-11-21
forum: General Help
---

### Post by dragos240 on 2009-11-21
i want to rm everything inside a file, i did:
locate xfce > output.txt

now I want to delete all the files listed inside that file.

I tried:
rm 'cat output.txt'

I have no idea what to do.

---

### Post by sisco311 on 2009-11-21
```
man bash | less --pattern\="Command Substitution"
```

it's:
```
rm $(< filename)
```
or
```
rm `cat file`
```

---

### Post by Prodigal Son on 2009-11-21
```
rm $(cat files.list)

```

---

### Post by blazemore on 2009-11-21
rm -v $(cat files.list)

---

### Post by dragos240 on 2009-11-21
> **sisco311 said:**
> ```
man bash | less --pattern\="Command Substitution"
```it's:
```
rm $(< filename)
```or
```
rm `cat file`
```

thanks!

---

