---
title: "Help needed"
date: 2010-08-03
forum: General Help
---

### Post by Karlo1 on 2010-08-03
This isnt real problem so sry if Im spamming.

So is there any program that can "replace"  letters or numbers with each other like 3 for 1, 6 for 3 or something like that. Or is it hard or possible to make?

Tnx

---

### Post by endotherm on 2010-08-03
well it would be a pretty simple script, but would require a tiny bit of programming knowledge. 
can you be more specific about what you want to do?

---

### Post by prodigy_ on 2010-08-03
You can use sed to translate character sets.

Example (translating 1 to 3 and 3 to 6): ```
echo "1331example3131"|sed 'y/13/36/'
```
Output: ```
3663example6363
```

---

### Post by Karlo1 on 2010-08-03
Actually its for 1 game like hotkeys but usually .exe doesnt work here. So can u tell me where to make scripts in ubuntu??

And in order it should be replaced, right numbers are from numerical part of keyboard ( very complicated xD)

q=7
2=8
3=4
4=5
5=1
6=2

---

### Post by endotherm on 2010-08-03
interesting. so are you trying to remap keys or just change some letters and numbers in a text file or somthing?

global scripts usually go in /usr/sbin but I keep an sbin in my home for personal scripts. pretty much wherever you like, but be sure to enable the execute permission.

---

### Post by Karlo1 on 2010-08-03
Actually i installed this OS today and im still newb researching new things, so it would be nice if u could help me somehow, atleast give some tutoriaL, bcuz it takes few mins to pros to make it and i wouldnt be able to make it for few days atleast -_-

---

