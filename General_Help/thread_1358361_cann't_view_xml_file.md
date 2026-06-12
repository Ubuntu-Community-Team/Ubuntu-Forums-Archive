---
title: "cann't view xml file"
date: 2009-12-18
forum: General Help
---

### Post by mIXpRo on 2009-12-18
hi ,
i have some xml files on my system (someone gave them to me) , when i try to open them in firefox i get the source code see attachment below .


how this can be solved ?

---

### Post by prem1er on 2009-12-18
This is what an [xml]("http://www.w3schools.com/xml/default.asp") file is. What are you tying to do with it, edit? If so, you need to right click the file and open with a text editor.

---

### Post by mIXpRo on 2009-12-18
i figured out whats the problem .
but anyway prem1er.

---

### Post by KeLa on 2009-12-18
Problem is exactly what your browser says in top of screen.
You need style sheet file and in beginning of xml something like this
```
<?xml-stylesheet alternate="yes" title="compact" href="small-base.css"
type="text/css"?>

```

This stylesheet file will provide information to browser's xml parser how to show the document.

---

