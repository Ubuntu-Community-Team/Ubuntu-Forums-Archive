---
title: "Code required to turn vertical list into horizontal list with spaces between words!"
date: 2009-08-16
forum: General Help
---

### Post by Rytron on 2009-08-16
Hi.
Does anyone know a command or some code that would turn a long list such as this:
[B]anagramarama
armagetron
barrage
brutalchess
burgerspace
bygfoot
ceferino[/B]

into this format:
**anagramarama armagetron barrage brutalchess burgerspace bygfoot ceferino**

Thank you.

---

### Post by Finalfantasykid on 2009-08-16
Give me a few minutes and I'll wip up a Java program to do this...

---

### Post by Bachstelze on 2009-08-16
A Java program? Jeez...

```
firas@iori ~ % cat test.txt
foo
bar
baz
foobar
foobaz
foobarbaz
firas@iori ~ % sed 'H;g;s/\n//1;s/\n/\ /g;' test.txt | tail -n 1
foo bar baz foobar foobaz foobarbaz

```

---

### Post by Finalfantasykid on 2009-08-16
> a java program? Jeez...yup :D

---

### Post by mali2297 on 2009-08-16
Sed? Jeez...

```

$ cat test.txt 
anagramarama
armagetron
barrage
brutalchess
burgerspace
bygfoot
ceferino
$ fmt test.txt 
anagramarama armagetron barrage brutalchess burgerspace bygfoot ceferino

```

---

### Post by Bachstelze on 2009-08-16
> **mali2297 said:**
> Sed? Jeez...

```

$ cat test.txt 
anagramarama
armagetron
barrage
brutalchess
burgerspace
bygfoot
ceferino
$ fmt test.txt 
anagramarama armagetron barrage brutalchess burgerspace bygfoot ceferino

```

You, sir, just won an internets.

---

### Post by lswb on 2009-08-16
cat file|tr '\n' ' '

---

### Post by Rytron on 2009-08-16
Thank you Finalfantasykid, HymnToLife & mali2297. That was a rapid response.
:)

---

### Post by Bachstelze on 2009-08-16
> **lswb said:**
> cat file|tr '\n' ' '

Nice try, but...

```
firas@iori ~ % cat test.txt | tr '\n' ' '
foo bar baz foobar foobaz foobarbaz %
```

you also removed the terminating newline.

---

### Post by DaithiF on 2009-08-16
Hi,
another way:
cat testfile | tr '\n' ' '

---

### Post by lswb on 2009-08-16
> **HymnToLife said:**
> Nice try, but...

```
firas@iori ~ % cat test.txt | tr '\n' ' '
foo bar baz foobar foobaz foobarbaz %
```

you also removed the terminating newline.

I didn't see that requirement in the OPs specification :)

---

### Post by mali2297 on 2009-08-16
My solution seems to have been somewhat hasty. The **fmt** command wraps lines at 75 characters by default. You can change it to a maximum of 2500 characters (on my system) by using the **-w** flag:
```

fmt -w2500 test.txt

```

---

### Post by Rytron on 2009-08-17
> **mali2297 said:**
> My solution seems to have been somewhat hasty. The **fmt** command wraps lines at 75 characters by default. You can change it to a maximum of 2500 characters (on my system) by using the **-w** flag:
```

fmt -w2500 test.txt

```

Excellent!

---

