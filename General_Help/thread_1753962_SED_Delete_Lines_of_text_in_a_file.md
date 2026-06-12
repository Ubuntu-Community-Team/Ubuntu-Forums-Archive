---
title: "SED Delete Lines of text in a file"
date: 2011-05-09
forum: General Help
---

### Post by GreenDance on 2011-05-09
Hi, could someone tell me please, how to delete lines 5,6,7,8,9 from file **gd** using SED.

Thank You

Green Dance

---

### Post by DaithiF on 2011-05-09
Hi,
```
sed '5,9d' gd

```
will output to the console, add the -i inplace flag or redirect to a new file when happy its doing the right thing.

ie.
```
sed -i '5,9d' gd

```
or
```
sed '5,9d' gd > newfile

```

---

### Post by GreenDance on 2011-05-09
> **DaithiF said:**
> Hi,
```
sed '5,9d' gd

```
will output to the console, add the -i inplace flag or redirect to a new file when happy its doing the right thing.

ie.
```
sed -i '5,9d' gd

```
or
```
sed '5,9d' gd > newfile

```

Hi,

Thank You Very Much

Regards.

GreenDance

---

