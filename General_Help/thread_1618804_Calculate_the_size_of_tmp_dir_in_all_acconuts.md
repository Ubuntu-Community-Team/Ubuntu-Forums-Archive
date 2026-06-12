---
title: "Calculate the size of tmp dir in all acconuts"
date: 2010-11-11
forum: General Help
---

### Post by OOzypal on 2010-11-11
Hello

How can I calc the size of the tmp directory in all account. Do the following will calc each dir alone

```
du -sh /home/*/tmp
```

TIA

---

### Post by sisco311 on 2010-11-11
Use the -c flag:
```
du -csh /home/*/tmp
```
or
```
du -csh /home/*/tmp | awk '{if ($2 == "total") print $1}'
```

---

