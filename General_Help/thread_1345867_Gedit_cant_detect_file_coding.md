---
title: "Gedit cant detect file coding?"
date: 2009-12-04
forum: General Help
---

### Post by mac666 on 2009-12-04
hey
My gedit doesnt like to open many files...

If i try to open some log.txt file, gedit says:
"gedit cant detect charecter coding"
"Current: Current Local (UTF-8)"

(translated from swedish)

notepad how ever, can read the file without any problems...
This happens to MAny files, specially .txt files... how come? :|

edit: Notepad is the wine version of windows notepad...

---

### Post by hwttdz on 2009-12-04
I assume you've tried changing the region?  

Otherwise you can 
cat -v file.txt newfile.txt
gedit newfile.txt

What this does is replace all the characters you can't get.

---

