---
title: "Double characters in SED"
date: 2010-07-18
forum: General Help
---

### Post by 5ive on 2010-07-18
I wrote the command in SED:
```
echo abcdfghijklmn | sed 's/\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)\(.\)/\2\4\6\8\**10**\**11**\**12**\**13**/'
```
I received:
```
> bdgia**0a1a2a3**
```
I wanted this:
```
> bdgi**klmn**
```
What did I do wrong?

---

### Post by DaithiF on 2010-07-18
Hi,
I guess theres a max of 9 grouped expressions, when you ask for \10 you're actually getting the first \1, and a 0

try this instead:
```
$ echo abcdfghijklmn | sed 's/.\(.\)/\1/g'
bdgikmn

```

---

### Post by 5ive on 2010-07-18
But little. I can group ;/

---

