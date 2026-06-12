---
title: "quick question for Linux's &quot;sort&quot; function"
date: 2012-09-04
forum: General Help
---

### Post by lethalfang on 2012-09-04
Usually, "sort" will sort 10, 11, 12 ahead of 2, 3, 4. 
To sort by number, you can simply do "sort -n."

I have a slightly more complicated problem. 

I have files that begins with chr1, chr2, chr3, ..., chr10, chr11. 
How do I sort it, so that chr2, chr3, ... will be sorted ahead of chr10, chr11?

Thanks in advance.

---

### Post by drmrgd on 2012-09-05
Try it with the -V option as such:

```
$ cat chrtest.txt 
chr1
chr11
chr3
chr5
chr7
chr23
chr15
chr6
chr8
chr13
chr14
chr9

$ sort -V chrtest.txt 

chr1
chr3
chr5
chr6
chr7
chr8
chr9
chr11
chr13
chr14
chr15
chr23
```

---

### Post by lethalfang on 2012-09-05
> **drmrgd said:**
> Try it with the -V option as such:

```
$ cat chrtest.txt 
chr1
chr11
chr3
chr5
chr7
chr23
chr15
chr6
chr8
chr13
chr14
chr9

$ sort -V chrtest.txt 

chr1
chr3
chr5
chr6
chr7
chr8
chr9
chr11
chr13
chr14
chr15
chr23
```

Thanks. "sort -V" works exactly as I wanted.

---

