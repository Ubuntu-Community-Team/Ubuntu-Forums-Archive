---
title: "how to merge two text files via terminal"
date: 2010-09-18
forum: General Help
---

### Post by neoargon on 2010-09-18
I wish to combine two text files 1.txt and 2.txt . 1.txt contains the word good . 2.txt contains the word morning . I wish to create another file 3.txt by merging 1.txt and 2.txt(ie 3.txt should contain the word goodmorning ) .I tried the following code
```
touch 3.txt
cat 1.txt 2.txt >3.txt
```

it produces a file containing
good
morning

But what I need is goodmorning ,without space or new line between good and morning

Can anybody please help?

---

### Post by lykeion on 2010-09-19
You could pipe it through tr command to remove space and newlines in the files, like this:
```
cat 1.txt 2.txt | tr -d [:space:] > 3.txt
```

---

