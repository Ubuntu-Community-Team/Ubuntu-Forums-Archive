---
title: "echoing path"
date: 2009-12-31
forum: General Help
---

### Post by sandyd on 2009-12-31
im trying to make a bash script to add
```

export PATH=$PATH:/home/"*username*"/dev/depot_tools

```
to a user's bash rc

ive currently got to 
```

echo "export PATH=$PATH:/home/"$(whoami)"/dev/depot_tools" >> ~/.bashrc

```
but echo keeps on parsing $PATH which i dont want.
is there some way to stop it from parsing it?

---

### Post by chewearn on 2009-12-31
One way: put a backslash before $PATH:
```

echo "export PATH=\$PATH:/home/"$(whoami)"/dev/depot_tools" >> ~/.bashrc

```

Another way: use single quote instead of double:
```

echo 'export PATH=$PATH:/home/'$(whoami)"/dev/depot_tools" >> ~/.bashrc

```

---

### Post by sandyd on 2009-12-31
> **chewearn said:**
> One way: put a backslash before $PATH:
```

echo "export PATH=\$PATH:/home/"$(whoami)"/dev/depot_tools" >> ~/.bashrc

```Another way: use single quote instead of double:
```

echo 'export PATH=$PATH:/home/'$(whoami)"/dev/depot_tools" >> ~/.bashrc

```
thanks!

---

