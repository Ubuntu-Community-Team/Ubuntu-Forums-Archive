---
title: "Nauitilus isn't displaying correctly"
date: 2009-11-21
forum: General Help
---

### Post by Cardale on 2009-11-21
I am using Ubuntu 9.10 and I was trying to arrange my files by type which I believed meant exstension, but ubuntu or gnome doesn't arrage it that way. It arrages items by type as long as it knows what that type is if it doesn't then it lumps all the of unknowns together. Even the known file types get lumped together with other ones.

My question is this.  How can I arrange my files in my directories by .*(exstension)?

---

### Post by hwttdz on 2009-11-21
That wasn't terribly clear, maybe you can give an example, like

file1.type1
file2.type1
file3.type1
file4.type1
file5.type1
file6.type1
file1.type2
file2.type2
file3.type2
file4.type2

and maybe put file3 and file4 in there where nautilus places them and where you think it should?

---

### Post by wojox on 2009-11-21
Just right click in the directory and choose Arrange Items > Type.

You have to give it an Extension to be grouped with the others.

---

### Post by Cardale on 2009-11-21
I don't know if you have attempted that yourself or not, but if the extension is unknown to linux it gets grouped with all the other unknowns even though the .ext isn't the same.

Example

.ext1  Unknown
.ext2  Unknown

or even

.tpl  Plain Text Document
.txt  Plain Text Document

They group these together even though they are not the same type of files.  They are in the same format, but they are not the same EXTENSION.

Get what I'm saying?  Surprisingly windows behaves this way.  Windows doesn't care if the .ext is unknown it will group it with the same extension.

---

### Post by Cardale on 2009-11-21
bump

---

### Post by hwttdz on 2009-11-21
Two things, one you waited like an hour to bump a thread, that's not really necessary.  Second, this is not nautilus "not behaving correctly" it's just that you think that the proper behavior should be something different than what the developers think the proper behavior is.  Did you try any of the alternative applications?  It's possible that nautilus has a file types database, which may be in the nautilus documentation (which I really have no desire to read), in which case you could just make the change to the database file.  So I suggest bonding with the documentation [http://live.gnome.org/Nautilus](http://live.gnome.org/Nautilus)

---

### Post by Cardale on 2009-11-22
Thats why I am asking you haha.  Well me and the developers should have a talk because a file could be plain text and still not be the same as another file. One could be script that isn't compiled or a recipe for cooking your moms favourite dish which I did enjoy last time I had it.  :D

---

### Post by hwttdz on 2009-11-22
There's always
"ls|sort -k2 -t."

---

