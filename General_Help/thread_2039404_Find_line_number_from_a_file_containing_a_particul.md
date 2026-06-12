---
title: "Find line number from a file containing a particular text"
date: 2012-08-08
forum: General Help
---

### Post by sd@ksu on 2012-08-08
I have a file "file" in this structure (say):
[HTML]
#S 1 bla bla
#C bla bla
#Q bla bla
#L x y z
0 1 2
1 2 5
2 5 7
#R bla bla

#S 2 bla bla
#C bla bla
#Q bla bla
#L x y z
0 1 2
1 2 5
2 5 7
#R bla bla

#S 3 bla bla
#C bla bla
#Q bla bla
#L x y z
0 1 2
1 2 5
2 5 7
#R bla bla
[/HTML]

I want to find the line number of the lines containing "#S 1" , "#S 2" , "#S 3" and than pass it as a variable in a bask script. How do I achieve that?

---

### Post by sd@ksu on 2012-08-08
I can use grep, it seems as below: 
```

grep -n "#S 1 " file

```

but I want only the line number...also is there a better way to do it?

---

### Post by steeldriver on 2012-08-08
you can just follow the grep by a 'cut' I think:

```
grep -n "#S 1 " file | cut -d':' -f1
```

---

### Post by Vaphell on 2012-08-08
if you want to pass all numbers to your script in one go
```
./script $( grep -n '^# [1-3] ' file | cut -d: -f1 )
```

---

### Post by sd@ksu on 2012-08-08
works like a charm...thanks to both of you!:popcorn:

---

### Post by codemaniac on 2012-08-09
An awk sulution for you . ;)

```
 awk '/#S [0-3]/{print NR}' input_file
```

---

### Post by sd@ksu on 2012-08-15
codemaniac..yup..learning awk...bte..liked ur progress quote at bottom..:guitar:

---

