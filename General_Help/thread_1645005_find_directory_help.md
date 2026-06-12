---
title: "find directory help"
date: 2010-12-14
forum: General Help
---

### Post by COKEDUDE on 2010-12-14
I am looking for the directory ".Private". Can someone tell me why my first search does not work?
```
~ $ sudo find / -iname -type d ".Private" 2>/dev/null
```


And why does this one work?
```
~ $ sudo find / -type d -iname '.Private' 2>/dev/null
/media/4fa4e92e-3532-48fd-a83d-6ea340a669b6/.ecryptfs/bob/.Private

```

---

### Post by susema on 2010-12-14
You don't have to use sudo. You can search with;

```
find ~ -iname '*.Private*' -print
```

---

### Post by nothingspecial on 2010-12-14
> **COKEDUDE said:**
> I am looking for the directory ".Private". Can someone tell me why my first search does not work?
```
~ $ sudo find / -iname -type d ".Private" 2>/dev/null
```
And why does this one work?
```
~ $ sudo find / -type d -iname '.Private' 2>/dev/null
/media/4fa4e92e-3532-48fd-a83d-6ea340a669b6/.ecryptfs/bob/.Private

```


because in the first one, you didn`t put the name of the directory you were searching for immediatelyafter the  after the -iname option.

---

