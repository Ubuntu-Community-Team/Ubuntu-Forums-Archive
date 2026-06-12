---
title: "How to generate a list with files and folders"
date: 2011-02-02
forum: General Help
---

### Post by PrvSAT on 2011-02-02
Hello,

Does anyone know if there is an application available to generate a list with files and folders from a location, like a hard drive or a folder? The list could be in any format, even a text file would be just fine. 
Thank you for reading this.

---

### Post by mcduck on 2011-02-02
I don't know about any application for this purpose, but this will do the trick from a terminal:
```
ls -R /path/to/your/location > ~/Desktop/list.txt
```

---

### Post by Morbius1 on 2011-02-02
```
tree
```If you want it to go to a file:
```
tree > tree.txt
```If you want to specify a specific location:
```
tree /path-to-directory
```

---

### Post by PrvSAT on 2011-02-02
Thank you very much, I will try it. :)

---

