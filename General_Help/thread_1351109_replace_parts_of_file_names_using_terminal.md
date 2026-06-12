---
title: "replace parts of file names using terminal"
date: 2009-12-10
forum: General Help
---

### Post by xir_ on 2009-12-10
Hey guys i have looked around for a solution to this but so far i haven't found anything that is to my satisfaction (if easy or explanation).

Does anyone know how to substitute part of a file name for every file in a folder.

eg:
fe_mal_pbe0_epr_svp_somf.inp

to

fe_mal_b3lyp_epr_svp_somf.inp

or in perl speak
```
s/pbe0/b3lyp/ig
```


Now i know how to use the mv command, but i don't quite understand how you do a regex type substitute.


So this can be done in pearl quite easily but i am looking for a bash type answer.

---

### Post by kaibob on 2009-12-10
If I understand correctly, every file name contains pbe0 and you want to replace it with b3lyp? If so, you can use the rename command:

```
rename -n 's/pbe0/b3lyp/' *
```

The -n option tells rename to do a dry run and report proposed changes. Substitute -v for -n to actually make the changes.

---

### Post by pbrane on 2009-12-10
**man rename** This is a command that can use sed|perl type **s/oldpat/newpat/** syntax.

sed may be an alternative as well.

---

### Post by xir_ on 2010-10-15
> **kaibob said:**
> If I understand correctly, every file name contains pbe0 and you want to replace it with b3lyp? If so, you can use the rename command:

```
rename -n 's/pbe0/b3lyp/' *
```

The -n option tells rename to do a dry run and report proposed changes. Substitute -v for -n to actually make the changes.

I just wanted to add this can be done similar to above using

```
rename [start] [replacement] *

```

---

