---
title: "bash white space help"
date: 2009-11-13
forum: General Help
---

### Post by prem1er on 2009-11-13
I have a text file of account numbers on each line of the file. The problem is that there is a bunch of white space in the beginning of the file that is slowing another process down for me.  How can I remove the white space at the beginning of the file, without removing white space between account numbers. For example...


```




00232
23840282
H 3232 1341
3241
34324 2342
```

I just want to remove the white space up to the first account number.  Thanks.

---

### Post by alphaniner on 2009-11-13
```
$ cat file

00232
23840282
H 3232 1341
3241
34324 2342




$ cat file |**sed '/^$/d'** 
00232
23840282
H 3232 1341
3241
34324 2342
$

```

[sed one-liners]("http://www.unixguide.net/unix/sedoneliner.shtml")

Partial explanation: ^ means beginning of line, $ means end of line.  So the pattern being matched (^$) is a line that has nothing between its beginning and its end.

---

### Post by prem1er on 2009-11-13
Thank you, so much.

---

### Post by ghostdog74 on 2009-11-13
```

awk 'NF' file

```

---

### Post by ghostdog74 on 2009-11-13
```

awk 'NF{f=1}f' file

```

---

### Post by alphaniner on 2009-11-13
Gah! I didn't fully read your request.  To just remove the blank lines from the beginning of the file, you want to use **sed '/./,$!d'**

```
$ cat file

00232
23840282
H 3232 1341
3241
34324 2342

13513684


$ cat file |sed '/./,$!d' 
00232
23840282
H 3232 1341
3241
34324 2342

13513684


$ 

```

---

### Post by ghostdog74 on 2009-11-13
> **alphaniner said:**
> 

$ cat file |sed '/./,$!d' 
$ 
[/CODE]

no need the useless cat

---

