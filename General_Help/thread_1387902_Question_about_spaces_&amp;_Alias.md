---
title: "Question about spaces &amp; Alias"
date: 2010-01-22
forum: General Help
---

### Post by Rytron on 2010-01-22
Hi.
Is it possible to open a file with alias and still have spaces in the file name?
For example, I have this file setup to open with alias:
[COLOR="DarkSlateBlue"]```
[COLOR="DarkSlateBlue"]alias mtd="openoffice.org ~/Documents/Movies-TV-Database.ods"[/COLOR]
```[/COLOR]
However I cannot open this file with alias; the only change is that I renamed the file to Movies & TV Database.ods:
```
[COLOR="Sienna"]alias mtd="openoffice.org ~/Documents/Movies & TV Database.ods"[/COLOR]
```

---

### Post by diesch on 2010-01-22
```
alias mtd='openoffice.org ~/"Documents/Movies & TV Database.ods"'
```

---

### Post by Ahriman on 2010-01-22
```
alias mtd="openoffice.org ~/Documents/Movies\ &\ TV\ Database.ods"
```
didn't work?

---

### Post by Rytron on 2010-01-23
Unfortunately none of the above worked! :(

---

### Post by diesch on 2010-01-23
What exactly doesn't work? Do you get any error messages?

---

### Post by Rytron on 2010-01-23
> **diesch said:**
> What exactly doesn't work? Do you get any error messages?

I got this error:
```
/home/rytron/Documents/Movies & TV Database.ods does not exist.
```

I click OK and then it opens a blank .odt file!

---

### Post by Rytron on 2010-01-23
> **Ahriman said:**
> ```
alias mtd="openoffice.org ~/Documents/Movies\ &\ TV\ Database.ods"
```
didn't work?

I get this error:
/home/rytron/Documents/Movies does not exist.

I click ok and a blank .odt file is opened! :(

**Correction**: Hi diesch. Actually your code does work. It was an error on my part. Thank you.

---

### Post by VCoolio on 2010-01-23
try it with a blackslash before the '&' character also. Also type the command in a terminal and use <tab> to autocomplete the filename and see what it looks like.

---

### Post by pbrane on 2010-01-23
this quoting works for me:

```
alias mtd='openoffice.org "/home/username/Documents/Movies & TV Database.ods"'
```
Make sure you use a complete path and put the path and filename in double quotes. put the entire alias in single quotes. And of course, replace username with your user name.

---

### Post by Rytron on 2010-01-24
> **pbrane said:**
> this quoting works for me:

```
alias mtd='openoffice.org "/home/username/Documents/Movies & TV Database.ods"'
```
Make sure you use a complete path and put the path and filename in double quotes. put the entire alias in single quotes. And of course, replace username with your user name.

Thank you pbrane. Works here also! :P

---

### Post by Rytron on 2010-01-24
> **diesch said:**
> ```
alias mtd='openoffice.org ~/"Documents/Movies & TV Database.ods"'
```

Works perfectly! :popcorn:

---

