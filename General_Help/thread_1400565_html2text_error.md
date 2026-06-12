---
title: "html2text error"
date: 2010-02-07
forum: General Help
---

### Post by gregarion on 2010-02-07
Hey guys, i just install html2text and when i ran the command

```
$html2text index.html > read.txt
```i get an error saying 
```

bash: read.txt: Permission denied
```what does this mean and how can i solve it?

---

### Post by Vishnu V on 2010-02-07
Permission denied means that you have don't have permission to create a file named read.txt on that directory 
You can solve this by using an administrative power
```
sudo su
sudo html2text index.html > read.txt

```
or you can save read.txt in a directory with write permission
eg
```

html2text index.html > ~/read.txt

```
it will save the file read.txt to homedirectory

---

