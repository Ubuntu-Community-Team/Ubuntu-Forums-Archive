---
title: "tr multiple tab"
date: 2009-10-25
forum: General Help
---

### Post by dandeliondream on 2009-10-25
```
kcc@ubuntu:~$ echo $VAR
jane,15,2000
kcc@ubuntu:~$ echo -e "$VAR" | tr "," "\t\t"
jane    15    2000

```I would like to replace the comma ','  with 2 tabs '\t\t' but it can only display one tab. How do i solve this problem?

---

### Post by kaibob on 2009-10-25
> **dandeliondream said:**
> ...I would like to replace the comma ','  with 2 tabs '\t\t' but it can only display one tab. How do i solve this problem?

I'm not familiar with the tr utility and can't answer your question directly. Have you considered using bash or another utility, such as sed?

```
echo jan,15,2000 | sed 's/,/\t\t/g'

word=jan,15,2000 ; echo -e ${word//,/\\t\\t}
```

---

### Post by dandeliondream on 2009-10-25
> **kaibob said:**
> I'm not familiar with the tr utility and can't answer your question directly. Have you considered using bash or another utility, such as sed?

```
echo jan,15,2000 | sed 's/,/\t\t/g'

word=jan,15,2000 ; echo -e ${word//,/\\t\\t}
```

Thanks, I've learnt something new today :popcorn:

---

